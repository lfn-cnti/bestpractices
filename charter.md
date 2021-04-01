# Cloud Native Network Function Working Group Charter

## Introduction
The goal of the Cloud Native Network Function Working Group (CNF WG)  is to aid companies such as telecom vendors, communications service providers and large scale enterprises, running internal telecommunications-like infrastructure, to better understand what cloud native means for telecommunications workloads and help build consensus around industry adoption of cloud native technologies (per CNCF TUG).

The CNF WG operates under the aegis of CNCF. The focus of the CNF WG is to define the process around evaluating the cloud nativeness of networking applications, aka CNFs, running on Kubernetes. We collaborate with the [CNF test suite project](https://github.com/cncf/cnf-conformance/blob/master/README-testsuite.md) who works on the mechanics of the tests.

The goals for the group are:
- To identify cloud native best practices for CNFs running on Kubernetes which CNF Developers and operators alike may adopt
- To determine which practices will allow networking applications to most effectively utilize Kubernetes capabilities and services


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


## Governance


### CNF WG Member Roles


#### Chairs

The CNF WG will be co-chaired by 3 people - one co-chair from the Kubernetes (K8s) Community, one from the Service Provider (SP) Community and one from the CNF Developer (Dev) Community - in order to maintain equal representation.

- *Primary role of Chairs is governance of the group.*
- The Chairs are responsible for ensuring that group meetings are facilitated effectively, while also engaging group members in leadership roles. Effective facilitation includes the following activities:
    - extending discussion via asynchronous communication to be inclusive of members who cannot attend a specific meeting time
    - scheduling discussion of proposals that have been submitted
    - asking for new proposals to be made to address an identified need
    - partnering with Technical Leads to establish a roadmap and manage ongoing projects

**Representation**

A maximum of one person from any one entity may hold a chair role at any given moment.  See the [Independence](#independence) section for further details.

#### Tech Lead

CNF WG has multiple tech leads who are recognized as (1) experts in the Networking, Telco, Kubernetes, and/or Cloud Native domains, (2) leaders of projects in these domains, and (3) demonstrating the ability to provide the balanced technical leadership required to produce the required unbiased outputs of the CNF WG. The reason for having separate chair and tech lead roles is to allow responsibility for primarily administrative functions to be separated from deep technical functions and associated time commitments and skill sets. Where appropriate, an individual may perform both roles as shown in CNF WG member roles.

Tech leads are primarily focused on the technical execution of the working group's activities including:
- Leading projects in the working group’s area. For example, building out a use case or developing a best practice.
- Applying their time and ability to deep technical dives on projects.

**Representation**

A maximum of one-third of the tech lead roles may be held by people from any one entity at any given moment.  See the [Independence](#independence) section for further details.


#### Everyone else (eg. other members)

Membership is self-declared.

There are no membership requirements to be a part of the CNF WG. This is an open public working group welcoming anyone who would like to help.

All members
- May either have no explicit roles or responsibilities, or formally assigned roles (see above).
- May not create the impression that they have any authority or formal responsibilities in the CNF WG other than assigned roles.

<!--
See [CONTRIBUTING](CONTRIBUTING.md) documentation for more information how to get involved.
-->

## Elections
Co-chairs and tech leads will be elected for one year terms and may run for reelection. 

The CNF WG employs "organization voting" to ensure no single organization can dominate the project.

Individuals not associated with or employed by a company or organization are allowed one vote. Each company/organization, or related group of companies (regardless of the number of maintainers associated with or employed by that company/organization), will have a maximum of one-third representation in votes.  If the results of an election result in greater than 1/3 representation, the lowest vote getters from any particular company will be removed until representation on the committee is less than one-third.

In other words, if two contributors are employed by Company X, two by Company Y, two by Company Z, and one maintainer is an un-affiliated individual, a total of four "organization votes" are possible; one for X, one for Y, one for Z, and one for the un-affiliated individual.

For the purpose of this document, “Company” shall mean any entity (Company-A) which controls or is controlled by another entity (Company-B) or which, together, is under the common control of a third party (Company-C), in each case where such control results from ownership, either directly or indirectly, of more than fifty percent of the voting securities or membership interests of the entity in question; and one “Company” is all of the entities that are each described above.

Each organization listed in the [interested parties document](interested-parties.md) has one vote. Interested parties can be added at any time, but must be added at least one week before any election to have a vote. Any contributor from an organization may cast the vote for that organization. Each organization can cast one vote for a co-chair candidate in each of the communities (Kubernetes (K8s) Community, Service Provider (SP) Community, and CNF Developer (Dev) Community), three total votes. Each organization can vote for as many tech leads as they see fit.

The chair for each community will be elected using [Ranked Choice Voting](https://en.wikipedia.org/wiki/Ranked_voting). Tech leads must win at least 60% of the votes cast to be elected.


<a name="independence"></a>
### Independence

The CNF WG strives to maintain its editorial independence from the companies and organisations that provide its members.  To this end, this charter sets limits on the involvement any given entity might have in its operation, in order to maintain the integrity of its output as a consensus view of industry technical experts.

To this end, representation from a single entity for a given role is limited, to avoid undue influence.  This section determines how companies, organisations and individual interested parties are determined to be independent of each other, and the way in which this affects elections.

#### Determination of independence

1. An entity consists of a single company or organisation, a related group of companies or organisations in common ownership, or an individual acting independently of their employment.

2. Entities may potentially not be independent if:

- an individual works for a company
- the ownership of two companies is not independent (one owns the other or they both are owned by a common parent, in part or in whole)
- an individual or company is under contract to another

3. If a member raises a concern of that two entities are not independent, or, conversely, that a single entity should be considered as two separate entities, the member shall make their case and the co-chairs will consider it.

4. If they deem the case valid, the relationship and its effects will be discussed by members.  The existence of a relationship does not necessarily demonstrate that the organisations are acting in concert.

5. A vote of all uninvolved members will be held to determine whether or not the multiple parties should be considered one entity under the rules of this charter.

#### Reconsidering the decision

The decision on independence or dependence of entities may be revisited after a period of not less than three months.  After this time, any member may raise it for discussion via the above process.

#### Change of affiliation

The affiliations of members can change over time, both through the above process and via job changes, mergers and divestments, and so on.

If, through this process, an entity becomes overrepresented, members of that entity will first be asked if they wish to resign their roles in order to remain within the allotment.

If insufficient members resign their roles, the positions held by members associated with that entity will all be put up for a special election. These positions are open both to previous holders and to any new nominees.  The standard nomination and election process shall be carried out.  Representatives elected though this process shall serve the remaining part of the current term.

#### Effect on representation

After any election, the results may indicate that a particular entity is overrepresented for a role, having won more seats than the limit.  In this event, the maximum number of the members belonging to that entity shall be calculated, and members belonging to the entity having the least votes will be excluded from the role until the entity is fairly represented.  Where there is a tie, a coin toss or other random selection mechanism shall be used to choose who is allocated the seat.

## PR Approval Process

Use cases and best practices need approval from at least two tech leads to be merged. Approval from three community members can substitute for one tech lead vote. Merging may be vetoed by the co-chairs with a vote of at least 2/3.

Charter updates need approval from at least two co-chairs. A co-chair vote can be replaced by the approval of two tech leads.

Changes to fix broken links, typos, small gramatical phrasing, or other editorial issues can be merged with the approval any co-chair or tech lead.
