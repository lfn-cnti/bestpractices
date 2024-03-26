# Contributing to the CNTI Best Practices Focus Area

Welcome to the Cloud Native Telecom Initiative (CNTI) Best Practices Focus Area! This is an open, public group welcoming anyone who would like to help identify cloud native best practices for networking applications. We're glad you're here!

To learn about this focus area, [read the wiki](https://wiki.lfnetworking.org/display/LN/Best+Practices).

Except as otherwise noted, the content of this repository is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/) ([local copy](LICENSES/CC-BY-4.0.txt)), and any code is licensed under the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0.html) ([local copy](LICENSES/APACHE-2.txt)). See more at [LICENSE.md](LICENSE.md).

## Where to Contribute

Contributors are encouraged to collaborate using the following resources:

- [Bi-weekly public community meetings](README.md#recurring-meetings)
  - Review [past meetings on the wiki](https://wiki.lfnetworking.org/display/LN/Best+Practices)
- [LFN Tech Slack](https://join.slack.com/t/lfntech/shared_invite/zt-2cfymedlz-358~927JZBYfVJRMA7P9jg)
    - **Channel**: #cnti-bestpractices
- LFN CNTI mailing list
  - <https://lists.lfnetworking.org/g/lfn-cnti>
- Pull Requests
  - <https://github.com/lfn-cnti/bestpractices/pulls>
- Issue Tracker
  - <https://github.com/lfn-cnti/bestpractices/issues>

## What to Contribute

We welcome many different types of contributions including:

- General improvements to documentation
- [Use cases](doc/use-case/) and user stories (these are used to provide context for and select best practices)
  - [See the template for more details](doc/use-case/NNNN-UC-template.md)
- Definitions
  - [Actors and Roles](https://github.com/lfn-cnti/bestpractices/discussions/30)
  - [Glossary](doc/glossary.md)
- [CNTI Best Practices](doc/best_cnf_dev.md)
  - [Process to publish a CNTI Best Practice](doc/cbpps/cnti_best_practice_process.md)
  - [See the template for more details](doc/cbpps/NNNN-cbpp-template.md)
- Gap Analysis

### Code Contributions

The CNTI Best Practices Focus Area doesn't develop any code, but its work feeds into many groups that do develop code both upstream and downstream. If you want to take the work of the CNTI Best Practices and put it into code, check out:

- [CNTI Test Catalog](https://github.com/cnti-testcatalog/testsuite) is the place for test cases used in best practices
- [Kubernetes Network Plumbing](https://github.com/k8snetworkplumbingwg) implements a common standard addressing how one may attach multiple networks to pods in Kubernetes
- [Kubernetes SIG Network](https://github.com/kubernetes/community/tree/master/sig-network) is responsible for the components, interfaces, and APIs which expose networking capabilities to Kubernetes users and workloads

## How to Contribute

### Come to Meetings

Absolutely everyone is welcome to come to any of our meetings. You never need an invite to join us. In fact, we want you to join us, even if you don’t have anything you feel like you want to contribute. Just being there is enough!

You can find out more about our meetings [here](https://github.com/lfn-cnti/bestpractices#meetings). You don’t have to turn on
your video. The first time you come, introducing yourself is more than enough. 

Over time, we hope that you feel comfortable voicing your opinions, ideas and providing feedback with the community. Sharing your own ideas, and experiences can help in ways you might not initially realize.

### Join a GitHub Discussion

- Go to the [GitHub Discussion board](https://github.com/lfn-cnti/bestpractices/discussions/)
- Participate in existing discussions
  - eg. [Defining actors and audiences](https://github.com/lfn-cnti/bestpractices/discussions/30)
- Add new discussion topics
- Reference Issues, PRs, and existing content from the [Best Practices repository](https://github.com/lfn-cnti/bestpractices)

### Find an Issue

Review, contribute to, create new [GitHub issues](https://github.com/lfn-cnti/bestpractices/issues).

We have good first issues for new contributors and help wanted issues suitable for any contributor. [good first issue](https://github.com/lfn-cnti/bestpractices/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) has extra information to
help you make your first contribution. [help wanted](https://github.com/lfn-cnti/bestpractices/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22) are issues suitable for someone who isn't a core maintainer and is good to move onto after your first pull request.

Sometimes there won’t be any issues with these labels. That’s ok! There is likely still something for you to work on. If you want to contribute but you don’t know where to start or can't find a suitable issue, you can reach out to one of the [co-chairs](GOVERNANCE.md#current-co-chairs).  

Once you see an issue that you'd like to work on, please post a comment saying that you want to work on it. Something like "I want to work on this" is fine.

### Submit Pull Requests

Pull Requests are always welcome, even for small fixes like typos. Check [What to Contribute](#what-to-contribute) above for more information about what kind of PRs we are looking for.

#### Pull Request Checklist

When you submit your pull request, or you push new commits to it, our automated systems will run some checks on your new contribution. We require that your pull request passes these checks, but we also have more criteria than just that before we can accept and merge it. We recommend that you check the following things locally before you submit your change:

- We use GitHub Actions to test all pull requests. We prefer that all tests succeed on a pull request before it is merged. This repository also contains a *Makefile* for running linting tasks locally. Executing `make lint` is another way to check your work before GitHub actions.

### Review/comment on Pull Requests

Reviews and comments on open [Pull Requests](https://github.com/lfn-cnti/bestpractices/pulls) are always appreciated.
Up to 3 approvals from the community are needed to merge PRs so your review is greatly appreciated.

<!-- markdown-link-check-disable -->
One of [our values](charter.md#values) is "Commit first, improve later". Once a commit has been made you can [make suggestions for changes directly in the PR](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/commenting-on-a-pull-request#adding-line-comments-to-a-pull-request) to help us move forward faster together.
<!-- markdown-link-check-enable -->

Where the comment is better expressed as a proposed change, the change can be made directly either by editing the file (right hand "..." -> "edit file" for larger changes, or the "document-with-+-" icon above the comment window for smaller ones).   The author can accept these changes directly, which is much easier for them than writing a change themselves.

#### Acceptance of PRs for merging

- Spelling, grammar, and new interested parties require 1 approval for merging
- Other changes with exception to those listed in the [Governance Additional Approval Items list](GOVERNANCE.md#additional-approval-items) may be merged after approval of 3 community reviewers.

#### Steps for creating a new PR

- Once you have made your change or added new content
- Ensure you are up to date with the `main` branch of the cnf-wg repository
- Open a new [Pull Request](https://github.com/lfn-cnti/bestpractices/pulls)
- Choose at least 3 reviewers OR choose a [co-chair](GOVERNANCE.md#chairs) who will find reviewers for you

#### Steps to accept a PR

1. Reviewers will review the PR and give their feedback: approve, request change, comment w/o approval
1. After required number of approvals from reviewers is reached the PR may be merged

Anyone with merge access can merge the PR after the item has been approved.

### Acceptance criteria for Contributions

Reviewers - Any community member

- Everyone in the community is able to and encouraged to do reviews. Anyone can be a part of the CNF WG community.

Minor changes:

- Spelling, grammar, and adding new interested parties require 1 reviewer

Majority of other changes:

- Other changes with exception to those listed in the [Governance Additional Approval Items list](GOVERNANCE.md#additional-approval-items) may be merged after approval of 5 community reviewers.

### Ask for help

The best way to reach us with a question when contributing is to ask on:

- The original GitHub issue
- [Our Slack channel](https://lfntech.slack.com/archives/C06GV4J8S5U)

## Express Your Interest

The CNTI charter contains a list of organizations that are interested in these efforts. To add your organization name, please submit a Pull Request to edit the [interested parties file](interested-parties.md).

## Code of Conduct

The CNTI community follows the [LF Code of Conduct](https://lfprojects.org/policies/code-of-conduct/).

## Thank you

Thank you for your participation. We appreciate your help and look forward to collaborating with you!
