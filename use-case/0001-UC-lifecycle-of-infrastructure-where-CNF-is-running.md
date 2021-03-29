# UC-0001: Lifecycle management of infrastructure where CNF runs

## Glossary
- CNF - Cloud Native Network Function
- Cloud Native Platform - A platform that exhibits cloud like properties on which a CNF runs. For this use case, Cloud Native Platform = Kubernetes cluster

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
Cloud Native Platform DevOps (CNPD) teams regularly perform lifecycle operations on Cloud Native Platforms. These operations include both updates (no breaking changes are expected) and upgrades (there is possibility of breaking changes). For agile teams, these changes happen frequently. An average of 2 times per month is not unheard of. For simplicity, with regards to this use case, we will assume that the Cloud Native Platform is a Kubernetes cluster hosting a CNF. In reality there are number of additional components involved.

The Kubernetes cluster in question is defined according to cloud native principles: declarative deployments and immutable infrastructure. As such, this means that changes are performed via rolling upgrades in following sequence:
- one fresh node gets created and joined to the cluster
- one of existing nodes gets tainted, then drained and finally eliminated from the cluster
- this process repeats until all old nodes are eliminated from the cluster and replaced with fresh nodes

This process is first executed in a test environment, followed by reference or staging environment and finally a production environment, with a predetermined time distance (typically 7-10 days). 

The CNPD team expect the ability to perform changes on infrastructure "in place", while a CNF is operating, and during regular working hours (no maintenance windows). They rely on the CNF DevOps team to detect anomalies within their CNFs, after changes to the infrastructure, and report them early. Ideally, in the test environment. Finally, the CNPD expects that if any anomalies are detected, both teams will jointly troubleshoot and eliminate them together. The end goal being that teams are able to proceed with infrastructure changes rapidly. 

The CNF DevOps team expects that changes on infrastructure will cause neither downtime of CNF in production nor significant and lasting degradation of its function or performance. They are capable, however; of tolerating some amount of temporary degradation to performance during a change management process (e.g. requested retries etc...)

## Expected behavior 
It is expected that a CNF copes well with situations when one or more nodes in the cluster are replaced with fresh nodes. A CNF should be capable of bearing, without visible impact on its own function or performance, the situations in which it's workloads are shifted to newly available nodes. It is an expected functionality, that a proper CNF is not tightly coupled to any single node in a cluster, or group of nodes in larger clusters.

A CNF should be automatically testable, with regards to its proper functionality, in a relatively short time after changes to the infrastructure. Ideally, in the test and reference environments, there would be nightly tests running. The CNF team would be informed each day what, if any, tests broke their CNF. This means that it shall have automated test coverage at the level of 100%.  

## Challenges and limitations with Kube-native approach
Most of today's (so called) CNFs are retrofitted VNFs that have been forklifted into the containers. They are frequently pinning the nodes. CNFs expect that the cluster nodes are long living, even highly available. In Kube-native approach cluster nodes are actually ephemeral and relatively short living. They exist typically for couple of days to couple of weeks. In such situation CNFs are implicitly requiring that infrastructure is mutable and that Cloud Native Platform DevOps team keeps uptime of the cluster nodes high. This is neither practical at scale of CSPs nor it is conformant to cloud native practices.

Also, most of CNFs today are following systems integrated approach. This means that integration of CNF version X with Platform version Y has been tested separately, possily as part of periodic "plug tests" or the certification procedures. It is typically CNF vendor to Platform vendor activity. Upstream is missed out in these certifications. Integrated systems approach and periodic integration testing with fixed versions unfortunately does not work in cloud native scenario where change is only constant. Versions of components are changing frequently and not upgrading means only accumulating the risks and technical debt which is very expensive from operations perspective. If changes are done less frequently they are typically bigger and bring higher probability of failures.

### Established practices to overcome challenges and limitations
N/A (tbd)

### What needs to be done differently in order to overcome challenges and limitations 
CNFs shall be written for cloud. This means that as boundary condition they shall assume that every node is ephemeral and short lived. They need to use native Kubernetes mechanisms to assure their own high availability in spite of dynamic nature of Kubernetes cluster in which they are running. They shall be able to recover from node failures and from node draining with marginal loss of traffic in the worst case and without visible impact on end customers or systems they serve.

Each CNF shall come with suite of tests and testing scenarios that CNF DevOps team can deploy in their continous testing pipeline to enable that CNF is certified daily on that particular infrastructure.
