# Cloud Native Network Function Working Group Charter

## Introduction
The goal of the Cloud Native Network Function Working Group (CNF WG)  is to aid companies such as telecom vendors, communications service providers and large scale enterprises, running internal telecommunications-like infrastructure, to better understand what cloud native means for telecommunications workloads and help build consensus around industry adoption of cloud native technologies (per CNCF TUG).

The CNF WG operates under the aegis of CNCF. The focus of the CNF WG is to define the process around evaluating the cloud nativeness of networking applications, aka CNFs, running on Kubernetes. We collaborate with the [CNF test suite project](https://github.com/cncf/cnf-conformance/blob/master/README-testsuite.md) who works on the mechanics of the tests.

The goals for the group are:
- To identify cloud native best practices for CNFs running on Kubernetes which CNF Developers and operators alike may adopt
- To determine which practices will allow networking applications to most effectively utilize Kubernetes capabilities and services

## Values
The CNF WG is driven by high technical standards, and these must be maintained. It is also important to take into account that multiple humans are participating in the project, and we must ensure that we all treat each other well. In this respect, we will honor the following values:

* **Inclusive is better than exclusive** -
Broadly successful and useful technologies require different perspectives and skill sets, which can only be heard in a welcoming and respectful environment. Community membership is a privilege, not a right. Community members earn leadership through effort, scope, quality, quantity, and duration of contributions to the technology and the community.

* **Evolution is better than stagnation** - 
The CNF WG is not meant to be a set in time standard. The best practices should continually evolve with state of the art in the Kubernetes and cloud native ecosystems. Community leaders also have a duty to find, sponsor, and promote new community members. Leaders should expect to step aside. Community members should expect to step up.

* **Commit first, improve later** - 
The community thrives on contribution. A PR or suggestion for a change will move the community forward faster. Healthy disagreements are important for technical excellence, and should be accompanied with a way to move forward. We will accept good contributions and continue to make them better later.

* **Pragmatism instead of politics** - 
Our best practice recommendations should be focused on bringing value in the real world rather than in the abstract / hypothetical. These best practices will have their basis in real-world applications and use cases.

* **Community over product or company**
We are here as a community first, with the common goal of bringing the benefits of cloud native best practices to all its members and users everywhere. Our recommended best practices should be broadly applicable and stand-alone independently.

* **Adherence to the [Code of Conduct](code-of-conduct.md)**



## Mission Statement
Cloud Native Network Function Working Group’s mission is to increase interoperability and standardization of cloud native workloads. It is committed to the following (aspirational) design ideals:
- Portable - Cloud native workloads run everywhere -- public cloud, private cloud, bare metal, laptop -- with consistent functional behavior so that they are portable throughout the ecosystem as well as between development and production environments.
- Meet users partway - Many applications today are not cloud native, but have been working in production for decades. The WG doesn’t just cater to purely greenfield cloud-native applications, nor does it meet all users where they are. It focuses on cloud-native applications, but provides some mechanisms to facilitate migration of monolithic and legacy applications.
- Flexible - The cloud native technology ecosystem can be consumed a la carte and (in most cases) it does not prevent you from using your own solutions in lieu of built-in systems.
- Extensible - Cloud native workloads should integrate into your environment and add the additional capabilities you need.
- Automatable -  Cloud native workloads should aim to help dramatically reduce the burden of manual operations. They support both declarative control by specifying users’ desired intent via an API, as well as imperative control to support higher-level orchestration and automation. The declarative approach is key to the ecosystem’s self-healing and autonomic capabilities.
- Advance the state of the art - While the WG intends to drive the modernization of non-cloud-native applications, it also aspires to advance the cloud native and DevOps state of the art, such as in the participation of applications in their own management. Workloads should not be bound by the lowest common denominator of systems upon which they depend, such as container runtimes and cloud providers.

## In Scope
- Definition of Cloud Native Network Function (CNF)
- Cloud native best practices for the development and operations of CNFs
  - Provide a list of the cloud native benefits a best practice provides
  - Including dataplane CNFs
- Process around evaluating if best practices are used by a CNF
- Feedback into other related groups and specification bodies to improve CNF use cases (e.g. SIG App Delivery, SIG Networking, CNI)
- Publishing metrics/white papers
- General Recommendations

## Potential Future Scope
- Cloud native best practices for Telecom infrastructure (which run CNFs)

## Out of Scope

- Writing tests or a maintaining a test suite
- Building Tooling
- Promotion of specific tools
- Solving external dependencies


## Overlap and Relations with other Groups and Projects
The CNF WG sees itself as providing the upstream definition of what makes a networking application cloud native allowing downstream projects to create precise programs and/or implementations for their specific needs. This may include formal requirements or conformance tests/programs. Some of the groups who may utilize the program's deliverables are:

- Anuket Reference Stream 2 (Reference Architecture 2 (RA2), Reference Implementation 2 (RI2) and Reference Conformance 2 (RC2)) - is focused on Kubernetes-based platforms and basic interoperability between platform and workloads. Anuket R2 has not determined if workload cloud native requirements are in scope for Anuket Reference Stream 2. It is expecting CNCF to provide testing for the cloud native requirements it has defined.
- OVP 2.0 (Cloud Native) - is interested in leveraging an upstream source for cloud native requirements and test results (like deliverables from the CNCF CNF WG) to be used in the OVP 2.0 Badging Program.

Networking applications and the workloads that are created with them are related to many topics in Cloud Native computing; therefore this WG may collaborate with many of the other CNCF and K8s SIGs, WGs, and projects. A few of the groups with potential interactions/collaboration are:

- CNCF SIG App Delivery
- CNCF SIG Security 
- CNCF SIG Network
- Kubernetes SIG Apps
- Kubernetes SIG Testing
- K8s Conformance WG

## Responsibilities and Deliverables

Responsibilities

The CNCF community, through CNF WG, is in charge of what it means to be a Certified cloud native workload -- with a focus on networking and telecom workloads. 
The CNF WG creates and maintains the definitions, processes, as well as policies around the certification program. It determines what best pratices and cloud native principles are required to be conformant.

The work on the mechanics of the tests, implementation of tests which evaulate cloud native best practices, and the test framework itself occurs in [CNF test suite project](https://github.com/cncf/cnf-conformance/blob/master/README-testsuite.md) itself -- not in the working  group.

Deliverables
- Cloud native principles - framework documentation for cloud native best practices 
- Networking application cloud native best practices - including documentation, test definitions, best pratices
- Cloud native network function best practice program
