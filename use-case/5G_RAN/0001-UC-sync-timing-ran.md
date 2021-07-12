# UC-0001: Synchronization/Timing in Telco CNF world

  

## Glossary

> RAN - Radio Access Network
> DU - Distributed Unit support RLC, MAC, Physical layers
> CU - Centralized Unit support SDAP, RRC, PDCP protocol layers
> RU - Radio Unit
> gNB - gNodeB
- PTP - Precision Time Protocol

  

## Involved processes

- [x] Development
- [x] Deployment
- [x] System integration
- [x] Network integration
- [ ] Lifecycle management
- [x] Operations

  

## Involved actors / personas

  

> Business customer of CSP
Operations Team of CSP
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

> 3GPP 5G gNB have a flexible architecture to support a wide range of deployments. The gNB can be split into CU, DU, and RU. The CU provides the support of a higher layer protocol stack(Layer 3 and above). The DU runs a lower-layer protocol stack(L1, L2), and RU does the radio and Low-PHY processing. The DU requires real-time performance and strict timing or synchronization to perform all the Layer 1, Layer 2 processing and scheduling.

> To meet 5G requirements and processing demands, the network nodes must be synchronized. There are different ways to distribute the timing, like through GPS or any master PTP clock in the network with IEEE 1588v2 PTP.

> In a non-virtualized network(DU/CU), the entire monolithic stack runs directly on ASIC or hardware at line rates, which aids in maintaining the synchronization/timing.

> In container-based virtualized systems(vDU/vCU) or CNFs, the platform manages the workloads. In cloud native design, a monolithic vDU or vCU would result in many individual workloads. 5G has critical timing/synchronization requirements because of new services, new architectures and new technologies[1]. A time sync of ~1.5 microseconds or less is required to support the new spectrum and RAN features/applications[2]. The workloads need to maintain tight synchronization to meet such requirements.

> The nature of the telco workload is compute-network intensive, demanding real-time performance. The orchestration platforms need to support CNFs to meet their timing synchronization requirements.

  

## Expected behaviour

  

> The cloud native platform should be able to maintain the synchronization/timing of the telco workloads.

  

## Challenges and limitations with Kube-native approach

  

> The K8s egress/ingress gateway is limited to web-based traffic. They are not aware of time stamped packets, like PTP packets. These packets are time-critical and they do not identify or process differently. The existing gateways might introduce a delay for many unknown reasons during the distribution of synchronization/timing packets to workloads. This unwanted delay may lead the workloads to lose their synchronization. The IEEE 1588v2 PTP have taken care of such scenarios of loss of synchronization, but the container platform may lack the capabilities internally that can enable the workloads to manage their synchronization/timing.

  

### Established practices to overcome challenges and limitations

  

> To be developed

  

### What needs to be done differently in order to overcome challenges and limitations

  

> Kubernetes could have a time-sensitive gateway or a particular gateway that keeps track of synchronization/timing distributed from the network or GPS to workloads. This would help workload maintain their synchronization across the network. There could also be a correction mechanism internally in the platform to maintain the synchronization/timing.

  

### References

> [1] [https://wsts.atis.org/wp-content/uploads/sites/9/2018/11/2-01_China-Mobile_Li_5G-Synchronization_v5.pdf](https://wsts.atis.org/wp-content/uploads/sites/9/2018/11/2-01_China-Mobile_Li_5G-Synchronization_v5.pdf)

> [2] [https://www.ericsson.com/en/blog/2019/8/what-you-need-to-know-about-timing-and-sync-in-5g-transport-networks](https://www.ericsson.com/en/blog/2019/8/what-you-need-to-know-about-timing-and-sync-in-5g-transport-networks)
