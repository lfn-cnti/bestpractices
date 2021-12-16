<!-- Created from CBPP template v1.0
     Major: changes when we add or remove sections or demands for information
     Minor: changes when we alter formatting without changing content requirements
     Keep the first line of this comment in your best practice,
     to help us track formatting updates -->

# **CBPP-NNNN: Your short, descriptive title (TEMPLATE)**

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
  - [Alternatives (Optional)](#drawbacksalternatives)
- [Test Plan](#test-plan)
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

CNFs should be compliant with applicable best practices, and ops processes
should be validated for compliance with them.  However, compliance is a
journey, and we expect end users to start with little compliance and
improve over time.

Compliance is most useful when users, auditors and so on can identify
exactly _how_ and _why_ you are compliant.  If they test your compliance,
and their tests flag problems, they can see that this is intentional, and
they can find out why compliance is not possible.  They can see why you
chose not to be compliant and whether this non-compliance is acceptable to
them.  They can also review any mitigating steps you might propose for this
non-compliance or work out steps or their own.

If your team builds a component used in NFV, or operates a component
of NFV, this document explains how you document your compliance
status.  We recommend you make this best practice a part of your
delivery process.  This should be the very first best practice you attempt
to comply with.

## **Motivation**

Best practices do not always coincide with pragmatic design.  For whatever
reason, a best practice may not be applicable to your circumstance; it
may be too expensive to implement; it may even be technologically
impossible based on other constraints.

Our task as a working group is to help CNF users do _better_, by painting a
picture of a perfect world and explaining how teams can progressively
take steps towards it.  We want to help people on the journey.  And during
that journey, their components and processes will be imperfect.

By understanding that exceptions are going to exist, we make it possible
for teams to understand their shortcomings and document them.  Where
exceptions to specific best practices are frequent, this will also
feed back into improvements to our best practice recommendations.

### **Goals**

* Let users explain which best practices they are compliant with
* Communicate the level of compliance of individual parts of the system,
  both software and process level
* Let users use CNF-WG best practices even if they cannot be compliant
  with every single recommendation
* Help users reduce the number of exceptions over time

### **Non-Goals**

* Providing a specific file format for the documentation
* Requiring extensive documentation of each element - we will keep
  required information to a minimum
* Preventing delivery of components where non-compliance exists - we want
  teams to be able to deliver components that are good enough, even if they
  cannot be perfect
* Documenting processes for improving compliance - we recommend teams
  regularly review their compliance list, but we do not mandate any specific
  method and this will depend on the team and their working structure

## **Proposal**

We document a means of listing compliance and what elements should be
included in any record of non-compliance.

We describe when and how those lists should be shared and updated.


### Format examples

A simple machine-readable format might be a table in CSV format.  This
can contain the records described, and is conveniently machine-readable.

... example here ...

Making machines conveniently machine-readable, such as records of compliance
and non-compliance as simple booleans, helps consumers in filtering these
records and even building compliance checks into their acceptance tests.
Similarly, using a standard encoded format for the CNF-WG best practice
names helps to relate the compliance record back to a specific release
and version, and can ensure that all best practices in a release have been
considered and documented.


### Compliance of a CNF


## **Workload Context**

### **User Stories (Optional)**

#### **Story 1**

#### **Story 2**

### **Notes/Constraints/Caveats (Optional)**

### **References**

### **Alternatives (Optional)**

## **Testing Objectives**

## **Scoring**

- Mandatory (yes/no):
- Passing score (eg. +5):
- Failing score (eg. -1):

> Note: CBPP may have different priorities and importance leading to different scores

## **Implementation History**
