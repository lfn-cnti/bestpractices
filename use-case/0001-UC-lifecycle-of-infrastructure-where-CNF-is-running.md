# UC-0001: Lifecycle management of infrastructure where CNF runs

## Glossary
- CNF - Cloud Native Network Function
- Cloud Native Platform - Platform that exhibits properties of the cloud on which CNF runs. For this use case Cloud Native Platform = Kubernetes cluster

## Involved processes
- [ ] Development
- [ ] Deployment
- [ ] System integration
- [ ] Network integration
- [x] Lifecycle management (infrastructure)
- [x] Operations

## Involved actors / personas
- Cloud Native Platform DevOps
- CNF DevOps

## Involved system entities
- Cloud Native Platform
- CNF
- CI/CD/Testing
- Monitoring

## Situation
Cloud Native Platform DevOps team is regularly performing lifecycle operations on Cloud Native Platform. These operations are updates (no breaking changes are expected) or upgrades (there is possibility of breaking changes). There are happening in average 2 times per month. For simplicity of use case here we assume that Cloud Native Platform is the Kubernetes cluster in which a CNF is running. In reality there are number of additional components involved.

The Kubernetes cluster in question is defined according to cloud native principles: declaratively and immutably. This means that changes are done as rolling upgrade in following sequence:
- one fresh node gets created and joined to the cluster
- one of existing nodes gets cordoned, than drained and finally eliminated from the cluster
- this process repeats until all old nodes are eliminated from the cluster and replaced with fresh nodes

This process is first done in test environment, followed by reference and finally production environment with certain time distance (typically 7-10 days). 

Cloud Native Platform DevOps team expects that they can do the changes on infrastructure "in place", while CNF is operating, and in regular working hours (no maintenance windows). They count that CNF DevOps team can detect anomalies on CNF after changes on infrastructure and report them early, ideally in test environment. Finally they expect that if anomalies are detected they can jointly troubleshoot and eliminate them together with CNF DevOps team in order to proceed with infrastructure changes asap. 

CNF DevOps team expects that changes on infrastructure will not cause neither downtime of CNF in production nor significant and lasting degradation of its function or performance. They could however tolerate some temporary degradation of performance during process of change (e.g. some request retries etc)

## Expected behaviour
It is expected that CNF copes well with situations when one or more nodes in the cluster are replaced with fresh nodes with same or better capabilities. Assuming that cluster still offers enough suitable capacity to reschedule CNF pods elsewhere, the CNF shall be capable to bear, without visible impact on its function or performance, the situations in which its workloads are shifted to the other available nodes. If the cluster does not offer enough capacity, CNF shall still function, with graceful degradation of performance in the worst case. It is expected that propper functioning of CNF is not tight with any particular node of in the cluster or group of nodes in bigger clusters. To provide its full function or performance CNF can still demand certain type of nodes with particular capabilities (e.g. SR-IOV, GPU etc.). However it is not expected that shifting CNF pods dynamically from one node of such type to another node of the same type causes any problems for CNF or traffic it serves.   

CNF shall be automatically testable for its propper functioning in relatively short time after infrastructure change. Ideally, in test and refference environments there shall be nightly tests running and CNF team would be informed on next day if some tests broke CNF. This means that it shall have automated test coverage at the level of 100%.  

## Challenges and limitations with Kube-native approach
Most of today's (so called) CNFs are retrofitted VNFs that are packed in the containers. They are frequently pinning the nodes. VNFs expect that the cluster nodes are long living, even highly available. In Kube-native approach cluster nodes are actually ephemeral and relatively short living. They exist typically for couple of days to couple of weeks. In such situation CNFs are implicitely requiring that infrastructure is mutable and that Cloud Native Platform DevOps team keeps uptime of the cluster nodes high. This is neither practical at scale of CSPs nor it is conformant to cloud native practices.

Also, most of CNFs today are following systems integrated approach. This means that integration of CNF version X with Platform version Y has been tested separately, possily as part of periodic "plug tests" or the certification procedures. It is typically CNF vendor to Platform vendor activity. Upstream is missed out in these certifications. Integrated systems approach and periodic integration testing with fixed versions unfortunately does not work in cloud native scenario where change is only constant. Versions of components are changing frequently and not upgrading means only accumulating the risks and technical debt which is very expensive from operations perspective. If changes are done less frequently they are typically bigger and bring higher probability of failures.

### Established practices to overcome challenges and limitations
N/A (tbd)

### What needs to be done differently in order to overcome challenges and limitations 
CNFs shall be written for cloud. This means that as boundary condition they shall assume that every node is ephemeral and short lived. They need to use native Kubernetes mechanisms to assure their own high availability in spite of dynamic nature of Kubernetes cluster in which they are running. They shall be able to recover from node failures and from node draining with marginal loss of traffic in the worst case and without visible impact on end customers or systems they serve.

Each CNF shall come with suite of tests and testing scenarios that CNF DevOps team can deploy in their continous testing pipeline to enable that CNF is certified daily on that particular infrastructure.
