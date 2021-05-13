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

- Cloud Native Platform DevOps (CNPD)
- CNF DevOps

## Involved system entities

- Cloud Native Platform
- CNF
- CI/CD/Testing
- Monitoring

## Situation

Cloud Native Platform DevOps (CNPD) teams regularly perform lifecycle operations on Cloud Native Platforms. These operations include both updates (no breaking changes are expected) and upgrades (there is possibility of breaking changes). For agile teams, these changes happen frequently. An average of 2 times per month is not unheard of. For this use case, we will assume that a Kubernetes cluster is the Cloud Native Platform which is hosting the CNF. In reality there are number of additional components involved.

The Kubernetes cluster in question is defined according to cloud native principles: declarative deployments and immutable infrastructure. As such, this means that changes are performed via rolling upgrades in following sequence:

- one fresh node gets created and joined to the cluster
- one of existing nodes gets tainted, then drained and finally eliminated from the cluster
- this process repeats until all old nodes are eliminated from the cluster and replaced with fresh nodes

This process is first executed in a test environment, followed by reference or staging environment and finally a production environment, with a predetermined time distance (typically 7-10 days).

The CNPD team expect the ability to perform changes on infrastructure "in place", while a CNF is operating, and during regular working hours (no maintenance windows). They rely on the CNF DevOps team to detect anomalies within their CNFs, after changes to the infrastructure, and report them early. Ideally, in the test environment. Finally, the CNPD expects that if any anomalies are detected, both teams will jointly troubleshoot and eliminate them together. The end goal being that teams are able to proceed with infrastructure changes rapidly.

The CNF DevOps team expects that changes on infrastructure will cause neither downtime of CNF in production nor significant and lasting degradation of its function or performance. They are capable, however; of tolerating some amount of temporary degradation to performance during a change management process (e.g. requested retries etc...)

## Expected behavior

It is expected that a CNF copes well with situations when one or more nodes in the cluster are replaced with fresh nodes with same or better capabilities. Assuming that remaining capacity of the cluster is allowing rescheduling CNF pods to other, equivalent nodes, the CNF should be capable of bearing, without visible impact on its own function or performance, the situations in which its workloads are shifted to those nodes. If, within the course of infrastructure lifecycle operations, the capacity of the cluster gets reduced but remains above minimally allowed level, CNF shall still function with graceful degradation of its performance in the worst case. It is an expected functionality, that a proper CNF is not tightly coupled to any single node in a cluster, or group of nodes in larger clusters. CNF can still demand that nodes with certain capabilities are present (e.g. SR-IOV, XDP, GPU etc). However it shall not have issues nor impact for the customers if its workloads are dynamically shifted by kube-scheduler from one to another node of such type.

A CNF DevOps team shall be in position to quickly determine if CNF is behaving and functioning properly after lifecycle operation (i.e. change) on infrastructure is done. If all is ok it is confirmation that it is ok to promote that change to next environment and ultimately to the production. With the normal lifecycle pace of Cloud Native Infrastructure CNF DevOps team needs to count that this has to be done 4-6 times a month for all transitions between the environments. Ideally, it shall be happen automatically with combination of application testing and monitoring where the results can be available next day to CNF DevOps team. If that is not feasible it would still be acceptable if CNF DevOps team does that within 7 days per lifecycle operation.

## Challenges and limitations with Kube-native approach

Most of today's (so called) CNFs are retrofitted VNFs that have been forklifted into the containers.  The forklifted CNF is frequently tightly coupled to the underlying infrastructure, including going as far as assigning the CNF to a specific node. This means CNF workloads are blocking these nodes from being drained in reasonably short timeframe. These type of CNFs expect that the individual cluster nodes are long living, even highly available. In Kube-native approach cluster nodes are actually ephemeral and relatively short living. They exist typically for couple of days to couple of weeks. In such situation CNFs are implicitly requiring that infrastructure is mutable and that Cloud Native Platform DevOps team keeps uptime of the cluster nodes high. This is neither practical at scale of CSPs nor it is conformant to cloud native practices.

Also, most of CNFs today are following systems integrated approach. This means that integration of CNF version X with Platform version Y has been tested separately, possibly as part of periodic "plug tests" or the certification procedures. It is typically CNF vendor to Platform vendor activity. Upstream is missed out in these certifications. Unfortunately, systems integrated approach and periodic integration testing with frozen versions, do not work in cloud native scenario where change is only constant. Versions of components are changing frequently and not upgrading means only accumulating the risks and technical debt. This is very expensive from operations perspective. If changes are done less frequently they are typically bigger and bring higher probability of failures.

### Established practices to overcome challenges and limitations

N/A (tbd)

### What needs to be done differently in order to overcome challenges and limitations

CNFs shall be written for cloud. This means that as boundary condition they shall assume that every node is ephemeral and short lived. They need to use native Kubernetes mechanisms to assure their own high availability in spite of dynamic nature of Kubernetes cluster in which they are running. They shall be able to recover from node failures and from node draining with marginal loss of traffic in the worst case and without visible impact on end customers or systems they serve.

Each CNF shall come with a suite of tests, testing scenarios and monitoring rules that CNF DevOps team can leverage. A team can deploy the test suite tooling via their continuous testing pipeline and integrate the results with their monitoring systems. The end goal being to ensure that a CNF is verified and certified (the best case being daily) on that particular state of infrastructure.
