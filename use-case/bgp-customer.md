# BGP on a customer network

## Overview

A service provider wishes to run a BGP server that is attached to a customer network.  This is a common use case when using VPNs.

The customer network is a separate network from the internet, having its own addressing domain (i.e. it is a VRF on the service provider network).  In order to provide BGP service to this network, the BGP application run by the BGP server must peer with other BGP speakers on the customer network, and therefore needs to have an interface within that VRF.  Simultaneously, the BGP speaker will require a management interface (for configuration and telemetry) in the SP network.  The Kubernetes API endpoint will also be in the SP network, unavailable to the customer - the customer's network can _only_ access the BGP speaker.

<figure class="image">
<img alt="BGP network overview" src="./bgp-customer overview.svg" />
<figcaption>Figure 1: BGP network overview</figcaption>
</figure>

## Network consumption

In NFV we often consider interfaces that provide per-packet networking for the purposes of creating a fast dataplane.  This, however, is not one of those use cases.  Here, the BGP protocol involves a simple TCP connection, and the kernel network stack provides to the BGP process.  So, note that the BGP peering sessions will be socket-based connections and the BGP speaker will want to consume the network via standard BGP socket APIs (```socket()```, ```listen()``` and ```connect()```).

BGP speakers are true peers, without a client and a server.  Any BGP speaker is expected to listen on a well known port for its neighbours trying to connect.  At the same time, it will be attempting connections to those peers.

The BGP connection is typically described at both ends with the addresses of the opposite end.  The Kubernetes-based BGP speaker process will want to know, and reach, the address of its neighbour.  Similarly the neighbour will want to know, and reach, the address of the BGP speaker.  There is no DNS involved in this lookup.

## Problems vs standard Kubernetes

There are three sorts of networking occurring here.

1. We have the connection used by the OSS systems to the BGP speaker using the management VRF, which is isolated from the SP customer.
1. We have the connection used by the BGP peering sessions to the BGP speaker, using the customer VRF, isolated from other networks.
1. We have whatever internal networking is required between microservices within the BGP speaker (perhaps, for instance, speaker code versus a DB instance storing the RIB).

### CNI-mediated networking

Kubernetes' CNI interface provides for the internal connectivity - this has no fixed protocol and is likely amenable to the semantics of the CNI.  Similarly, the telemetry interface (logging, monitoring and configuration using e.g. a REST interface) will work using the CNI an Kubernetes ingress.

### Networking outside the scope of the CNI

However, the BGP interface will not work using the CNI, for a number of reasons.

#### Multiple VRFs

Kubernetes' CNI is designed to attach to the network outside of the platform using a single point of connectivity - basically, into a single VRF - and the defined APIs do not allow a different connection to be specified for other connections.  All CNI endpoints should be in a single addressing domain that can reach all other endpoints.

### Multiple VRFs attached to one process

Aside from this, if the BGP process is in two VRFs, it, and at least one of its pods, must attach to two routing tables.  This is conventionally done, in Linux, by using two namespaces.  This is problematic for stock Kubernetes.  It creates a namespace for each pod and gives control of it to the CNI, for the purposes of Kubernetes networking.  Kubernetes does not provide a means to create and attach a second namespace.

It is also not possible for an unprivileged container to change namespaces.  A process requires CAP_NET_ADMIN or higher privileges to switch namespaces.  However, CAP_NET_ADMIN is indiscriminate - a process with CAP_NET_ADMIN can do anything to any namespace on the server, regardless of whether it is assigned to the container in which the pod resides.

### BGP is not designed to be cloud-native

BGP far predates Kubernetes and it is not designed with cloud-style failure tolerance in mind.  Its connection is designed to be direct from one BGP process to another, with the assumption that the network provides reachability and nothing else.

BGP peers need to know their own address and the address of their peer.  Address rewrites (e.g. NAT) in the flow are likely to cause problems rather than help the solution.

BGP sessions last as long as the TCP connection is held up.  If the speaker process dies, the interruption in the connection causes a significant event on the network, and having a failover process to accept the connection, while still useful, is not going to avoid that network event and the major part of the disruption caused by the failure.

So: current BGP speakers are not going to be able to make use of standard forms of address rewriting (e.g. NAT) or load balancing from the platform, and in fact these features will cause problems if they cannot be avoided.  If BGP requires special network functionality it is likely to be specific to the application and therefore built into the application, not general purpose enough to be worth building into the platform.
