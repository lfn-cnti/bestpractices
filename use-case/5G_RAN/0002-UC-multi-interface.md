# UC-0002: Support of Multi-Communication Interface in Telco CNF world 

## Glossary

> RAN - Radio Access Network
> DU - Distributed Unit  support  RLC, MAC, Physical layers
> CU - Centralized Unit support SDAP, RRC, PDCP protocol layers
> RU - Radio Unit
> gNB - gNodeB
> IPC - Inter-Process Communication

## Involved processes

- [x] Development
- [x] Deployment
- [x] System integration
- [x] Network integration
- [ ] Lifecycle management


## Involved actors / personas

> Business customer of CSP
CNF Vendor
Cloud provider
Datacenter Operator/provider

## Involved system entities

>Data Center Network
Wide Area Network
Cloud Native Platform
CNF X
RAN
MANO

## Situation

> 3GPP 5G  gNB have a flexible architecture to support a wide range of deployments. The gNB can be split into CU, DU, and RU. The CU provides the support of a higher layer protocol stack(Layer 3 and above). The DU runs a lower-layer protocol stack(L1, L2), and RU does the radio and Low-PHY processing.  The DU requires real-time performance and strict timing/synchronization to perform all the Layer 1, Layer 2 processing and scheduling. 
> In a non-virtualized networks (DU/CU), the entire monolithic stack(DU), including the baseband processing, runs directly on ASIC or hardware to achieve real-time performance.
> Consider a DU, which runs the PHY, RLC, MAC layers of the protocol stack. In a monolithic black box non-virtualized DU, the interface between RLC and MAC is a proprietary interface and vendor-driven. This interface could be some form of IPC mechanism or a simple function call. The interface between PHY and MAC is FAPI/nFAPI, a open interface standardized by Small Cell Forum (SCF).  These proprietary interfaces, mainly designed for high-performance, low overhead, help to achieve real-time performance.
> In virtualized systems(vDU/vCU CNFs), the platform manages the workloads. With a cloud native design, the monolithic DU or CU would be split into many individual components as per the design, like workloads for different layers of the protocol stack, procedures, state management, user context storage, management and administration functionalities, etc.
> The nature of the telco workload is compute-network intensive, demanding real-time performance. An efficient and performance-driven communication interface between CNFs is required to meet the real-time performance.

> The Kubernetes model of Pod-to-Pod communication is network-based or IPC based. 
> Any network-based communication over IP between CNFs could lead to degradation in performance because of the additional communication overhead they create, like building a IP packet, processing through the network stack, in comparison with other IPC mechanisms. This could increase the latency between CNFs communication. 
>The native K8s supports IPC within the Pod and IP communication outside the Pod. It is not clear on the communication between Pods over IPC mechanisms.
>There is no support for vendors to plug their methods of communication between CNFs.

## Expected behaviour

> The cloud-native orchestration/container platforms should support the multiple IPC mechanisms and multiple IPC endpoints communication.
## Challenges and limitations with Kube-native approach

>Kube-native approach is suitable for IP based networking. The telco workloads might require IPC based mechanism for CNFs communication.

### Established practices to overcome challenges and limitations

> Not applicable

### What needs to be done differently in order to overcome challenges and limitations

>The K8s or container platforms can have plugin for IPC based communication like Multus CNI, enabling a POD to have multiple network interfaces. 
>A plugin for IPC might be required, enabling the POD/CNF to support multiple IPC based endpoints and mechanisms.
>There should be some provision for vendors to plug their IPC mechanisms.
