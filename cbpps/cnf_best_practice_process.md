# Process to publish a CNF Best Practice

## Table of Contents

* [Introduction](#introduction)
* [(Optional) Socialize the idea]()
* [Best Practices for CNF Developers](#best-practices-for-cnf-developers)


## Understand the Mission Statement

The goal of the Cloud Native Network Function Working Group (CNF WG) is to aid companies such as telecom vendors, communications service providers and large scale enterprises, running internal telecommunications-like infrastructure, to better understand what cloud native means for telecommunications workloads and help build consensus around industry adoption of cloud native technologies (per CNCF TUG).

It is important that the best practices that we produce work towards that goal.

Please read the [CNF-WG Charter](../charter.md) and in particular the [Mission Statement](../charter.md#mission-statement).

## (Optional) Socialize the idea

Once you're sure the best practice aligns with the mission statement, it's sometimes a good idea to socialise the idea with the working group to get input and different perspectives, or to help focus the best practice on a specific topic.

The working group has the following communication channels:
- [Github repo discussion board](https://github.com/cncf/cnf-wg/discussions)
- Add an agenda item in the [weekly meeting agenda](https://docs.google.com/document/d/1YFimQftjkTUsxNGTsKdakvP7cJtJgCTqViH2kwJOrsc/edit#)
- Start a conversation / thread in the [CNF-WF Slack Channel](https://cloud-native.slack.com/archives/C01F1LVAQCC)
- Send a message to the mailing list (https://lists.cncf.io/g/cnf-wg)

## Contribute the CNF Best Practice Proposal

### Read the Contributing Guide

Once you're ready to contribute the best practice, it's a good idea to read the [contributing guide](../CONTRIBUTING.md#how-to-contribute).

### Create a GitHub Issues for a specific best practice idea

Ideally a set of best practices will have their own tickets.
- First, check that there is not an existing issue ([open or closed](https://github.com/cncf/cnf-wg/issues?q=is%3Aissue)) covering the best practice suggestion.
  - If one is closed, then create a new issue and reference the old issue.
  - If an existing issue is currently open, add to the current issue unless the idea significantly changes it, in which case it should be in a new issue.
  - If an old suggestion was rejected, reference old issue and provide additional information on why the best practice should be reconsidered.

- Each best practice will be published and recommended (if accepted) individually.
  Example: "use least privileges for containers" is a high level set of best practices.  "Use non-root users in containers" is a single best practice.
- It is important as the submitter that you respond to comments in the issue to ensure the proposal doesn't become "stale".

### Create a Pull Request with the suggested CNF Best Practice

- Check that there is not an existing PR ([open or closed](https://github.com/cncf/cnf-wg/pulls?q=is%3Apr)) covering the best practice suggestion.
- Create a draft following the [template](cbpps/NNNN-cbpp-template.md) and existing best practices.
- Tag current CNF WG members to review.
- Note: PRs for related use stories and use cases can be created independently or combined with a suggested best practice as seems appropriate.

### Communicate the PR and work to get it accepted 

<!-- IDEA: Use welcome bot for first time contributors e.g. https://github.com/apps/the-welcome-bot -->

- Add the PR to upcoming [weekly CNF WG meeting agenda](https://docs.google.com/document/d/1YFimQftjkTUsxNGTsKdakvP7cJtJgCTqViH2kwJOrsc/edit#) to discuss and attend the meeting.
<!-- Idea: add checklist item “added PR to weekly agenda” to PR Template https://github.com/cncf/cnf-wg/blob/main/.github/PULL_REQUEST_TEMPLATE/pull_request_template.md -->
<!-- Idea: respond to 1st contributors with additional steps / details -->
- Respond to comments in the PR, and merge suggestions when agreed.
  - It is important to keep the PR active.
  - Because we're all volunteers, we try and keep the number of open PRs to a manageable level.
  - Therefore, co-chairs will look to close out PRs which have stalled with no progress and submitter is absent for more than 45/60 days.
<!-- IDEA: Include the stale bot into the repo e.g. https://github.com/probot/stale -->
- If the PR is rejected, the co-chair(s) will communicate with the contributor, document the reason for rejection, and follow up in the related issue.
- If the PR is accepted, it will be merged by one of the co-chairs.
  - The number of reviewers accepting is documented in the [Contributing file](https://github.com/cncf/cnf-wg/blob/main/CONTRIBUTING.md#steps-to-accept-a-pr).

### Add to the list of CNF Best Practices

Once the best practice PR has been accepted and merged, you can raise another PR to get the best practice added to the [CNF Best Practice List](../doc/best_cnf_dev.md).