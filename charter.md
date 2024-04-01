# Cloud Native Telecom Intiative Charter

## Introduction

The purpose of the Cloud Native Telecom Initiative (CNTI) is to aid companies including CNF vendors, Communications Service Providers and large scale enterprises to understand and adopt best practices for cloud native networking.  In doing so, the CNTI seeks to drive industry adoption of cloud native technologies.

The CNTI operates under the aegis of LF Networking. There are three (3) focus areas in CNTI which include:

**Best Practices** - defining cloud native and Kubernetes native best practices for telecom networking.

**Test Suite** - developing a vendor neutral and open source testing catalog that can be used to validate a CNF's adherence to community defined best pratices. 

**Certification** -  developing an open source and vendor neutral cloud native networking certification program where open and closed source networking applications can be certified. 

The goals for the CNTI are:

- Identify cloud native and Kubernetes native best practices for networking 
- Determine which practices will allow networking applications to most effectively utilize Kubernetes capabilities and services
- Develop a vendor neutral testing catalog that enables CNF Developers, Service Providers, and downstream projects to verify how well a CNF adheres to cloud native best practies
- Provide an open source and vendor neutral cloud native networking certification program

## Values

The CNTI is driven by high technical standards, and these must be maintained. It is also important to take into account that multiple humans are participating in the project, and we must ensure that we all treat each other well. In this respect, we will honor the following values:

- **Inclusive is better than exclusive** -
Broadly successful and useful technologies require different perspectives and skill sets, which can only be heard in a welcoming and respectful environment. Community membership is a privilege, not a right. Community members earn leadership through effort, scope, quality, quantity, and duration of contributions to the technology and the community.

- **Evolution is better than stagnation** -
The CNTI is not meant to be a set in time standard. The best practices should continually evolve with state of the art in the Kubernetes and cloud native ecosystems. Community leaders also have a duty to find, sponsor, and promote new community members. Leaders should expect to step aside. Community members should expect to step up.

- **Commit first, improve later** -
The community thrives on contribution. A PR or suggestion for a change will move the community forward faster. Healthy disagreements are important for technical excellence, and should be accompanied with a way to move forward. We will accept good contributions and continue to make them better later.

- **Pragmatism instead of politics** -
Our best practice recommendations should be focused on bringing value in the real world rather than in the abstract / hypothetical. These best practices will have their basis in real-world applications and use cases.

- **Community over product or company** -
We are here as a community first, with the common goal of bringing the benefits of cloud native best practices to all its members and users everywhere. Our recommended best practices should be broadly applicable and stand-alone independently.

- **Adherence to the [Code of Conduct](code-of-conduct.md)**

## Mission Statement

CNTI’s mission is to simplify the creation and consumption of CNFs by publicising best practices for their development and operation. It is committed to the following (aspirational) design ideals:

- Portable - Cloud native workloads run everywhere -- public cloud, private cloud, bare metal, laptop -- with consistent functional behavior so that they are portable throughout the ecosystem as well as between development and production environments.
- Meet users partway - Many applications today are not cloud native, but have been working in production for decades. The WG doesn’t just cater to purely greenfield cloud-native applications, nor does it meet all users where they are. It focuses on cloud-native applications, but provides some mechanisms to facilitate migration of monolithic and legacy applications.
- Flexible - The cloud native technology ecosystem can be consumed a la carte and (in most cases) it does not prevent you from using your own solutions in lieu of built-in systems.
- Extensible - Cloud native workloads should integrate into your environment and add the additional capabilities you need.
- Automatable -  Cloud native workloads should aim to help dramatically reduce the burden of manual operations. They support both declarative control by specifying users’ desired intent via an API, as well as imperative control to support higher-level orchestration and automation. The declarative approach is key to the ecosystem’s self-healing and autonomic capabilities.
- Advance the state of the art - While the CNTI intends to drive the modernization of non-cloud-native applications, it also aspires to advance the cloud native and DevOps state of the art, such as in the participation of applications in their own management. Workloads should not be bound by the lowest common denominator of systems upon which they depend, such as container runtimes and cloud providers.

## In Scope

- Definition of Cloud Native Network Function (CNF)
- Cloud native best practices for the development and operations of CNFs
  - Provide a list of the cloud native benefits a best practice provides
  - Including dataplane CNFs
- Process around evaluating if best practices are used by a CNF
- Feedback into other related groups and specification bodies to improve CNF use cases 
- Publishing metrics/white papers
- Writing tests and maintaining a test suite
- General recommendations

## Potential Future Scope

- Cloud native best practices for Telecom infrastructure (which run CNFs)

## Out of Scope

- Building Tooling
- Promotion of specific tools
- Solving external dependencies

## Overlap and Relations with other Groups and Projects

The CNTI sees itself as providing the upstream definition of what makes a networking application cloud native allowing downstream projects to create precise programs and/or implementations for their specific needs. This may include formal requirements or conformance tests/programs. Some of the groups who may utilize the program's deliverables are:

- Anuket Reference Stream 2 (Reference Architecture 2 (RA2), Reference Implementation 2 (RI2) and Reference Conformance 2 (RC2)) - is focused on Kubernetes-based platforms and basic interoperability between platform and workloads. Anuket leverages the CNTI test suite for testing the cloud native requirements it has defined.


Networking applications and the workloads that are created with them are related to many topics in Cloud Native computing; therefore this WG may collaborate with many of the other CNCF and K8s SIGs, WGs, and projects. A few of the groups with potential interactions/collaboration are:

- CNCF SIG App Delivery
- CNCF SIG Security
- CNCF SIG Network
- Kubernetes SIG Apps
- Kubernetes SIG Testing
- K8s Conformance WG

## Responsibilities and Deliverables

Responsibilities

The LF Networking community, through CNTI, is in charge of what it means to be a Certified cloud native workload -- with a focus on networking and telecom workloads.
The CNTI creates and maintains the best practice definitions, processes, as well as policies around the certification program. It determines what best practices and cloud native principles are required to be conformant.

Deliverables

- Cloud native principles - framework documentation for cloud native best practices
- Networking application cloud native best practices - including documentation, test definitions, best practices
- Cloud native network function best practice program
- Cloud native networking tests as part of the CNTI test suite
