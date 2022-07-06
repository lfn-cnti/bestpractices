# Governance

## CNF WG Member Roles

### Chairs

The CNF WG will be co-chaired by 3 people - one co-chair from the Kubernetes (K8s) Community, one from the Service Provider (SP) Community and one from the CNF Developer (Dev) Community - in order to maintain equal representation.

- *Primary role of Chairs is governance of the group.*
- The Chairs are responsible for ensuring that group meetings are facilitated effectively, while also engaging group members in leadership roles. Effective facilitation includes the following activities:
  - extending discussion via asynchronous communication to be inclusive of members who cannot attend a specific meeting time
  - scheduling discussion of proposals that have been submitted
  - asking for new proposals to be made to address an identified need
  - partnering with Technical Leads to establish a roadmap and manage ongoing projects

#### **Chairs - Representation**

A maximum of one person from any one entity may hold a chair role at any given moment.  See the [Independence](#independence) section for further details.

#### **Current Co-Chairs**

- Service Provider Co-Chair: Tom Kivlin, @tomkivlin
- CNF Developer Co-Chair: Victor Morales, @electrocucaracha
- Kubernetes Co-Chair: Taylor Carpenter, @taylor

Term runs 2022-07-01 to 2023-06-30

### Everyone else (eg. other members)

Membership is self-declared.

There are no membership requirements to be a part of the CNF WG. This is an open public working group welcoming anyone who would like to help.

All members

- May either have no explicit roles or responsibilities, or formally assigned roles (see above).
- May not create the impression that they have any authority or formal responsibilities in the CNF WG other than assigned roles.

<!--
See [CONTRIBUTING](CONTRIBUTING.md) documentation for more information how to get involved.
-->

## Elections

### Timeline

Co-chairs will be elected for one year terms and may run for reelection.

### Eligibility to Vote

The CNF WG employs "organization voting" to ensure no single organization can dominate the project.

Individuals not associated with or employed by a company or organization are allowed one vote. Each company/organization, or related group of companies (regardless of the number of maintainers associated with or employed by that company/organization), will have a maximum of one-third representation in votes.  If the results of an election result in greater than 1/3 representation, the lowest vote getters from any particular company will be removed until representation on the committee is less than one-third.

In other words, if two contributors are employed by Company X, two by Company Y, two by Company Z, and one maintainer is an un-affiliated individual, a total of four "organization votes" are possible; one for X, one for Y, one for Z, and one for the un-affiliated individual.

For the purpose of this document, “Company” shall mean any entity (Company-A) which controls or is controlled by another entity (Company-B) or which, together, is under the common control of a third party (Company-C), in each case where such control results from ownership, either directly or indirectly, of more than fifty percent of the voting securities or membership interests of the entity in question; and one “Company” is all of the entities that are each described above.

Each organization listed in the [interested parties document](interested-parties.md) has one vote. Interested parties can be added at any time, but must be added at least one week before any election to have a vote. Any contributor from an organization may cast the vote for that organization. Each organization can cast one vote for a co-chair candidate in each of the communities (Kubernetes (K8s) Community, Service Provider (SP) Community, and CNF Developer (Dev) Community), three total votes.

### Voting Procedure

The chair for each community will be elected using [Ranked Choice Voting](https://en.wikipedia.org/wiki/Ranked_voting).

## Independence

The CNF WG strives to maintain its editorial independence from the companies and organisations that provide its members.  To this end, this charter sets limits on the involvement any given entity might have in its operation, in order to maintain the integrity of its output as a consensus view of industry technical experts.

To this end, representation from a single entity for a given role is limited, to avoid undue influence.  This section determines how companies, organisations and individual interested parties are determined to be independent of each other, and the way in which this affects elections.

### Determination of independence

1. An entity consists of a single company or organisation, a related group of companies or organisations in common ownership, or an individual acting independently of their employment.

2. Entities may potentially not be independent if:
   - an individual works for a company
   - the ownership of two companies is not independent (one owns the other or they both are owned by a common parent, in part or in whole)
   - an individual or company is under contract to another

3. If a member raises a concern of that two entities are not independent, or, conversely, that a single entity should be considered as two separate entities, the member shall make their case and the co-chairs will consider it.

4. If they deem the case valid, the relationship and its effects will be discussed by members.  The existence of a relationship does not necessarily demonstrate that the organisations are acting in concert.

5. A vote of all uninvolved members will be held to determine whether or not the multiple parties should be considered one entity under the rules of this charter.

### Reconsidering the decision

The decision on independence or dependence of entities may be revisited after a period of not less than three months.  After this time, any member may raise it for discussion via the above process.

### Change of affiliation

The affiliations of members can change over time, both through the above process and via job changes, mergers and divestments, and so on.

If, through this process, an entity becomes overrepresented, members of that entity will first be asked if they wish to resign their roles in order to remain within the allotment.

If insufficient members resign their roles, the positions held by members associated with that entity will all be put up for a special election. These positions are open both to previous holders and to any new nominees.  The standard nomination and election process shall be carried out.  Representatives elected though this process shall serve the remaining part of the current term.

### Effect on representation

After any election, the results may indicate that a particular entity is overrepresented for a role, having won more seats than the limit.  In this event, the maximum number of the members belonging to that entity shall be calculated, and members belonging to the entity having the least votes will be excluded from the role until the entity is fairly represented.  Where there is a tie, a coin toss or other random selection mechanism shall be used to choose who is allocated the seat.

## Content Approval Process

To encourage contributions, the CNF WG has a more relaxed stance on changes and delegates the acceptance for most items to the community as outlined in [CONTRIBUTING.md](CONTRIBUTING.md). The small list of exceptions are listed below which require a more thorough decision making process to achieve our desired outcome of fair representation and technical excellence.

### Delegation of default changes to community

The process for accepting changes to content in the CNF WG repository (including adding new content) for any item not in the [Additional Approval Items list](#DD) below will follow the acceptance and approval process outlined in the [CONTRIBUTING guide](CONTRIBUTING.md).

### Changes requiring additional approval

Items in the Additional Approval Items list require further discussion and approval before being accepted. The decision making process for items in this list is TBD.

#### Additional Approval Items

1. This list
1. [Charter](charter.md)
1. [Governance](GOVERNANCE.md)
1. [Code of Conduct](code-of-conduct.md)
1. CNF WG "Approved" Best Practices
    - This would be Best Practices which the CNF WG promotes in an approved list. Eg. Baseline Best Practices
    - Proposing a best practice is encouraged with the default process. Marking it as accepted and listing it as a CNF WG approved Best Practice requires additional review and approval.
    - Potentially the [Best Practices for CNF Developers](doc/best_cnf_dev.md) will list only approved best practices or at least have a designation for which are approved vs another status.
