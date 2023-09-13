# **CBPP-0005: A CNF’s containers should have one process category**

- [Release Signoff Checklist](#release-signoff-checklist)
- [Summary](#summary)
- [Motivation](#motivation)
  - [Goals](#goals)
  - [Non-Goals](#non-goals)
- [Proposal](#proposal)
- [Workload Context](#workload-context)
  - [User Stories (Optional)](#user-stories)
  - [Notes/Constraints/Caveats (Optional)](#notesconstraintscaveats-optional)
  - [References](#references)
- [Test Plan](#testing-objectives)
- [Implementation History](#implementation-history)

## **Release Signoff Checklist**

Items marked with (R) are required for the proposed best practice to be included in a release.

- [ ] (R) CBPP approvers have approved the CBPP status as `implementable`
- [ ] (R) CBPP summary, motivation and best practice details are appropriately documented
- [ ] (R) Test plan is in place, giving consideration to CNF Test Suite input
- [ ] (R) Scoring has been determined
- [ ]   "Implementation History" section is up-to-date
- [ ]    Supporting documentation—e.g., additional design documents, links to mailing list discussions/SIG meetings, relevant PRs/issues, release notes

## **Summary**

A CNF’s microservice(s) should follow the single concern principle. To help achieve this goal, a CNF’s microservice(s) should have only one process type (or set of parent/child processes) per container. The process(es) in the container should not spawn other process types (e.g. executables) as a way to contribute to the workload but rather should interact with other processes through a microservice API.

In Docker's Advanced concepts documentation regarding running multiple services in a container the Docker community says: _“It’s best practice to separate areas of concern by using one service per container. That service may fork into multiple processes (for example, the Apache web server starts multiple worker processes). It’s ok to have multiple processes, but to get the most benefit out of Docker, avoid one container being responsible for multiple aspects of your overall application.”_ [#3](#references)

This will help the programmability and flexibility of CNFs and networks through:
- Improvements in scalability and responsiveness to service needs
- Offloading container orchestration and leveraging the platform's capabilities
- Reducing downtime risk in deployments and upgrades, increasing the speed of delivery of services
- Managing service concerns in independent units


## **Motivation**

Challenges we think this best practice can help solve:

- Life-cycle management
    - If you have more than one process type in a container, you will have to manage the lifecycle of the secondary concerns within the container, which effectively means creating an orchestrator within the parent process type, reducing the value of using the Kubernetes orchestration capabilities.
    - Resource utilization is likely to be less efficient in multi-concerned containers, as the container runtime will look to allocate infrastructure resources for all components rather than individual microservices requirements.
    - Response time of multi-concerned containers is increased as scaling is required for the combined services rather than the individual services needing scaling.
    - Upgrades causing interruption in many services and all their integration at once because none of the components in the system are independent 
- Security
    - CNFs with multi-concerned containers have a larger surface area for cyberattacks and production bugs
    - Security vulnerabilities in one process type affect all other processes in the same container
- Observability
    - Reduced visibility of communication and activity of services in the multi-concerned container, as the container runtime will only be monitoring the init process within the container for signals
    - Log messages from the multi-concerned container are more complex because they are from many different sources instead of a single process type
    - Difficulty in identifying which process a bug resides in increases as a result of multiple process types in a single container
- Software Development Cycle
    - A CNF with multiple maintainers (which can be different groups in an organization) can block each other’s development process when a CNF is tightly coupled
    - A high degree of test coverage with a complex and tightly coupled CNF is difficult to achieve
    - Enable "polyglot" software designs, where the decoupled entities are developed in entirely different frameworks and even computer languages


### **Goals**

- Life-cycle management
    - Increase the use of Kubernetes orchestration capabilities instead of using additional container orchestration solutions 
    - Align with microservice architectural practices for operations and development
    - Make it easier to scale multiple containers of a CNF to produce an efficient resource utilization and faster response:
        - Make it easier to reason the best way to scale a CNF based on anticipated load by reducing the complexity of service concerns and allowing focus on each container (or Pods) anticipated needs 
        - Support scaling individual processes of the same type for efficient resource utilization and faster response time for changes in service load (increasing/decreasing)
    - Simplify deployment, reduce risk in upgrades and support easier rollbacks by managing the process types (service concerns) independently and providing coarse-grained dependencies at the container level 
- Security
    - Reducing attack surface area in a CNF’s containers by limiting the number process types and their dependencies such as additional binaries/libraries 
    - Protect containers from interfering with one another by leveraging the container namespace system
    - Allow finer control of permissions
- Observability
    - Simplifying troubleshooting and readability of log output. It is easier to consume log messages and reason about their output when they come from one concern or process type as opposed to when they are interweaved with other concerns. This is even more true in a container that prints all log messages to standard out, such as described in the 12-factor cloud native app.
    - Improve ability to monitor CNF activity by exposing the inter-process communication
- Software Development Cycle
    - Enable better support for multiple development teams to maintain their own independent lifecycle(s)
    - Move towards loosely coupled components: 
        - Reduces the complexity of each individual component
        - Simplifies determining where code resides for a given piece of functionality
        - Increases the confidence in test coverage of individual components
        - Facilitates locating the root cause of problems by eliminating extra variables
        - Minimizes the risk of changes in one component causing problems with another component. 
    - Increase composability of the CNF and it’s component services
        - One concern, and therefore process type, per container is much easier to reason about because it is easier to share and verbally communicate about its contents digitally. This makes it easier to reuse in other projects
        - Loosely coupled containers with well defined service APIs increase interoperability with other CNFs as well as between a CNFs component services

### **Non-Goals**

- Best practices for CNFs communication with other processes through microservice APIs
- Best practices on process supervision and management
- Reduce risk issues from of home-grown process management systems
    - Security, Zombie processes, unknown failures
- Specifying implementation details of each component
- Specifying how a CNF should be split into individual micro services

## **Proposal**

A CNF with multiple concerns should split services (or process types) for each of its concerns into separate containers. Service dependencies should be handled between containers through well-defined interfaces. 

Pod specs for the CNF should provide scaling and monitoring information for each service running in different containers.

## **Workload Context**

All pod types should implement this best practice.

### **User Stories**

#### 5G applications needing high-degree of flexibility and automation

_“5G requirements range from enhanced mobile broadband to ultra-reliable, low-latency communications to massive machine-type communications. Various 5G applications will mix and match these characteristics, requiring a high degree of programmability and the ability to easily combine different functionalities.”_  from “Why Use Containers and CloudNative Functions Anyway?” by Muthurajan Jayakumar (M Jay) @ Intel 

Separating service concerns, represented by process types, into different containers supports the goal of flexibility and programmability allowing the developer to provide definitions for the services needs, including hardware requirements, and the CNF consumer to efficiently scale these 5G services while supporting the accommodation of any container specific needs. 

Separating service concerns also helps to support the automation goals of the 5G operators by providing a more composable CNF with well defined interfaces and coarse grained dependencies at the container level increasing confidence in the testing phases of their pipelines and lowering risk during upgrades. 


#### SMF with multiple services for communicating with the AMF, UPF, and PCF needing more responsive scaling and requiring more resources for its AMF and UPF communication

An SMF with different services providing the communication between AMF, UPF, PCF and other services in an environment where many new sessions are initiated and end during peak times. This may require scaling of the service responsible for communication with the AMF and UPF faster than the service communicating with the PCF. If the services are split into their own containers they can be scaled independently.  




![Session Management Function within a 5G Service-based Architecture](https://hackmd.io/_uploads/B1qwravAh.png)
_Source: https://techcommunity.microsoft.com/t5/azure-for-operators-blog/what-is-the-5g-session-management-function-smf/ba-p/3693852_



### **Notes/Constraints/Caveats**

“That service may fork into multiple processes (for example, the Apache web server starts multiple worker processes). It’s ok to have multiple processes, but to get the most benefit out of Docker, avoid one container being responsible for multiple aspects of your overall application.”


Ideally in a container the process 1 (init process) should be the single application running in the container, as the container runtime monitors the PID 1 application process and uses its signals to report events, knowing when a container has stopped. When multiple processes are started it is recommended to use a non-home-grown supervisor such as http://supervisord.org/.  See discussion here https://github.com/cncf/cnf-wg/discussions/264

Depending on the specifics of the implemented functionality, the resulting split may have requirements towards the locality of the resulting multiple containers. It may require certain functions to be deployed on the same worker node or allow for distributing them amongst different worker nodes. The cloud-native principles, and the need for a horizontal scaling does imply the latter, i.e. no locality restrictions. However, due to the specifics of the Telco workloads, such limitations might be necessary for the operation of the particular functionality.
In some cases, the workload distribution can span multiple data-centers and geographic locations. The edge deployments are exemplifying such application designs.

### Definitions
 

- Monolithic application - applications which do not separate concerns into microservices are considered monolithic
    - Monolithic CNF - a monolithic application focused on networking concerns
- Multi-concerned containers - a container having more than a single process type providing services for different concerns



### **References**

1. https://www.infoq.com/articles/cloud-native-network-functions-concern/
1. https://www.ibm.com/cloud/architecture/architecture/practices/cloud-native-principles
    - _“SoC (separation of concerns) - Single concern principle”_
1. https://docs.docker.com/config/containers/multi-service_container/
1. https://en.wikipedia.org/wiki/Single-responsibility_principle
1. https://developers.redhat.com/articles/2022/01/11/5-design-principles-microservices
1. https://www.ericsson.com/en/future-technologies/architecture/network-capabilities
_“As a step towards a fully autonomous network and achieving an intent-based management of a network, its architecture must be prepared by raising the level of abstraction in management with e.g., strong separation of concerns.”_
1. https://github.com/cncf/cnf-testsuite/blob/main/docs/LIST_OF_TESTS.md#single-process-type-in-one-container
    - RATIONALE - https://github.com/cncf/cnf-testsuite/blob/main/RATIONALE.md#to-check-if-the-cnf-has-multiple-process-types-within-one-container-single_process_type
1. https://www.tutorialworks.com/containers-single-or-multiple-processes/
1. https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/containers-and-cloud-native-functions-white-paper.pdf
1. https://techcommunity.microsoft.com/t5/azure-for-operators-blog/what-is-the-5g-session-management-function-smf/ba-p/3693852


## **Testing Objectives**

Validate if there are more than one process type running inside of a container

## **Implementation History**

Documentation:
  - First version: September 2023
Test: CNF Test Suite
  - First version: [July 2021](https://github.com/cncf/cnf-testsuite/commit/7dc8934e1f9bf643f503ca695f6685cb22b18975)
