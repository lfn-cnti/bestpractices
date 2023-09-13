<!-- Created from CBPP template v1.0
     Major: changes when we add or remove sections or demands for information
     Minor: changes when we alter formatting without changing content requirements
     Keep the first line of this comment in your best practice,
     to help us track formatting updates -->

# **CBPP-0001: CBPP Process**

- [Release Signoff Checklist](#release-signoff-checklist)
- [Summary](#summary)
- [Motivation](#motivation)
  - [Goals](#goals)
  - [Non-Goals](#non-goals)
- [Proposal](#proposal)
- [Workload Context](#workload-context)
  - [User Stories (Optional)](#user-stories-optional)
    - [Story 1](#story-1)
    - [Story 2](#story-2)
  - [Notes/Constraints/Caveats (Optional)](#notesconstraintscaveats-optional)
  - [References](#references)
  - [Alternatives (Optional)](#alternatives-optional)
- [Test Plan](#testing-objectives)
- [Scoring](#scoring)
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

A standardized development process for CNF Best Practices is proposed, in order to:

- provide a common structure for proposing Best Practices
- ensure that the motivation for a Definition is clear
- allow for the enumeration of testing milestones and graduation criteria
- persist project information in a Version Control System (VCS) for future generations
- support the creation of _high-value, user-facing_ information such as:
  - an overall roadmap
  - motivation for impactful changes
- reserve GitHub issues for tracking work in flight, instead of creating "umbrella" issues
- ensure community participants can successfully drive changes to completion while stakeholders are adequately represented throughout the process

This process is supported by a unit of work called a CNF Best Practice Proposal, or CBPP.

## **Motivation**

**Note: Motivation is something that stems from the past, it's the culmination of experiences that drive you to wanting to achieve a specific goal.**

In a blog post describing the [road to Go 2](https://blog.golang.org/toward-go2), Russ Cox explains:

“that it is difficult but essential to describe the significance of a problem in a way that someone working in a different environment can understand”

Without a standardized mechanism for describing important Cloud Native best practices and principles, the wider telco community could struggle to weave a coherent narrative explaining why a particular CNF Definition is important. Additionally, users running critical infrastructure on Kubernetes need a forward-looking roadmap in order to plan their adoption strategies.

The purpose of the CBPP process is to reduce the amount of "tribal knowledge" in our community. By moving decisions from a smattering of mailing lists, video calls, and hallway conversations into a well tracked artifact, this process aims to enhance communication and discoverability.

An important goal of the CBPP process is ensuring that the process for submitting the content is both clear and efficient. The CBPP process is intended to create high-quality, uniform design documents for the CNF WG to deliberate.

### **Goals**

**Note:  A goal is something directed at the future, it's something you wish to happen and you work on achieving that goal.**

Providing a standardized way for the community to propose and discuss Cloud Native Definitions

### **Non-Goals**

Being an unchangeable template that does not meet the current needs of the community

## **Proposal**

The definition of what constitutes a Cloud Native best practice or principle is a foundational concern for the CNF WG. If a definition would be described in either written or verbal communication to anyone besides the author or developer, then consider creating a CBPP. The exact size and scale of an average CBPP will be determined as the group begins its work.

## **CBPP Template**

The template for a CBPP is defined [here](./NNNN-cbpp-template.md).

## **Important Metrics**

It is proposed that the primary metrics that would signal the success or failure of the CBPP process are:

- how many "cloud native best practices and principles" are tracked with a CBPP
- CBPP rejection rate
- PRs referencing a CBPP merged per month
- number of issues open which reference a CBPP
- number of contributors who authored a CBPP
- number of contributors who authored a CBPP for the first time

## **Workload Context**

Context should be provided which includes the type of CNF, workload, and CNF component (eg. Pod, container, Operator) this best practice applies to. The context, of an individual best practice, should illustrate the specific type of workload most likely to take advantage of the benefits listed.

### **User Stories (Optional)**

#### **Story 1**

I want to propose a new Cloud Native best practice definition. I will fill out the create a PR in the CBPP folder to start the discussion around the Cloud Native Definition. With the template, I will be able to articulate my ideas to the community.

#### **Story 2**

I agree/disagree with a proposed Cloud Native best practice definition. After reading through the CBPP, I will be able to comment on the PR and contribute to the discussion around it.

### **Notes/Constraints/Caveats (Optional)**

This first structure is still WIP and should not be considered final. As the CNF WG begins to dive into their work, this format and process should be modified to meet the WG's current needs.

When applicable, it should also provide a warning if the practice would be a determent to a divergent type of workload.

### **References**

The CBPP process, as proposed, was essentially copied from Kubernetes KEP which are similar to the [Rust RFC process](https://github.com/rust-lang/rfcs) which itself resembles the [Python PEP process](https://www.python.org/dev/peps/pep-0001/).

### **Alternatives (Optional)**

Any process has the potential to engender resentment within the community or not fits its needs. There is a risk that the CBPP process as designed will need to be changed or retired completely.

The centrality of Git and GitHub within the CBPP process also may place too high a barrier to potential contributors. However, given that both Git and GitHub are required to contribute code changes to many projects today, perhaps it would be reasonable to invest in providing support to those unfamiliar with this tooling.

## **Testing Objectives**

This CBPP will not be tested by the CNF Test Suite.

## **Scoring**

CBPPs may have different priorities and importance leading to different scores. Passing and failing scores may be different for similar reasons. Some may be mandatory.

## **GitHub Issues vs. CBPPs**

The use of GitHub issues when proposing changes does not provide the CNF WG good facilities for signaling approval or rejection of a proposed change because anyone can open a GitHub issue at any time.

In addition to the challenge of managing issues over time, searching for text within an issue can be challenging. The flat hierarchy of issues can also make navigation and categorization tricky. Not all community members will be uncomfortable using Git directly, but it is imperative for our community to educate people on a standard set of tools so they can take their experience to other projects they may decide to work on in the future. While git is a fantastic version control system (VCS), it is neither a project management tool nor a cogent way of managing a backlog. This proposal is limited to motivating the creation of a standardized definition of work in order to facilitate project management. This primitive for describing a unit of work may also allow contributors to create their own personalized view of the state of the project while relying on Git and GitHub for consistency and durable storage.

## **Implementation History**

The first version of this template was created before KubeCon NA 2020.
