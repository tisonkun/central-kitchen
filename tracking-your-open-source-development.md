---
title: Tracking Your Open Source Development
date: 2021-06-29 14:03:00
tags:
    - Open Source Program Office
    - Project Management
---

We contribute to the open-source software for bug fixes, enhancements, or new features.

Many contributions, including bug fixes and documentation improvements, can be implemented and reviewed via the normal GitHub pull request workflow.

Some contributions though are "substantial", and it is often required that these be put through a bit of a design process and produce a consensus among the community.

If the community reaches a consensus on the proposal, then the working group starts developing. So how do you in the working group track your open source development in this case?

A widely recognized practice is tracking issues. That says every accepted proposal has an associated issue tracking its implementation in the corresponding repository.

<!-- more -->

## What is a tracking issue?

So what is a tracking issue? A tracking issue is a GitHub issue that captures the planned and ongoing work of a proposal. This artifact is a medium used for planning, progress check-ins, and stakeholder communication.

You can take a look at the following tracking issues as examples.

* [Proposal: Support temporary table](https://github.com/pingcap/tidb/issues/24169)
* [Proposal: Reduce the Entropy of TiKV Community Governance](https://github.com/tikv/community/issues/118)

As you can see, the tracking issue is an overall board to all subtasks construct the whole proposal.

## How to create a tracking issue?

Formerly, when working on GitHub, we must maintain a tracking issue and its subtasks manually or based on third-party services. 

Fortunately, a few days ago GitHub releases its native support for tracking issues. Thus, you can break issues into actionable tasks by GitHub out-of-the-box today.

See also the blog [Introducing the new GitHub Issues](https://github.blog/2021-06-23-introducing-new-github-issues/) for more information and [Project planning for developers](https://github.com/features/issues) for user documentation.

The proposal above [Proposal: Reduce the Entropy of TiKV Community Governance](https://github.com/tikv/community/issues/118) is a living example of this functionality.

## What to be populated into the tracking issue?

Let's take a look at three examples and discuss what to be populated into the tracking issue.

1. [Proposal: Support temporary table](https://github.com/pingcap/tidb/issues/24169)
2. [Proposal: Reduce the Entropy of TiKV Community Governance](https://github.com/tikv/community/issues/118)
3. [Tracking issue for edition-specific preludes](https://github.com/rust-lang/rust/issues/85684)

### Issus or Pull Request

The first question is issue or pull request, which one is tracked by the tracking issue.

Example 1 and 3 links to both of them at the same time, while example 2 only link to subtasks in issue form.

If you ever live with other issue tracking tools such as [Jira](https://www.atlassian.com/software/jira), the preference is undoubtedly issue. There are at least three reasons you are supposed to track development with issues.

First, issues focus on the requirement, while pull requests focus on the implementation. On the one hand, discussions of an issue are generally about motivation, behavior, and compatibility. On the other hand. discussions of a pull request are generally about the code, its implementation, its style, and subtle details. Obviously, results delivered by development are mainly discussed in the first form, and if we mix all discussions in pull requests, they will be fragmented.

Second, an issue is a valid subtask, while a pull request is an attempt. That is, an issue can be referred to by a series of attempts to resolve it. So actions called back when an issue resolved, such as its fixed version, its resolution, and its release note, are better to be associated with an issue instead of a pull request because you are unsure whether the pull request a good fit and all these actions may be all in vain.

Finally, it is a technical blocker that the new GitHub Issue only supports issues as subtasks to be tracked. I think it is because the GitHub team considers as above and makes the decision to guide its users to use issues for tracking the development.

### Design Document 

So, we need a design document, right? Yes.

Every open source project takes design document a significant role, whatever they refer to this concept -- design document, RFC, proposal, etc.

Bidirectional links between design documents and tracking issues are admirable. The rationale is that the design document is the root of abstraction, while the tracking issue is the root of implementation. A tracking issue must be associated with a design, and an effective design must have a tracking issue.

Example 1 and 3 set up bidirectional links properly, while example 2 is more about community governance so that the design document is actually inlined to the tracking issue. We are talking about development but the new feature provided by GitHub is at the cutting edge so that I cannot find a living example. Sorry.

The design document also guides how its tracking issue separates the whole development task into subtasks. You can take a look at [the design document of example 1](https://github.com/pingcap/tidb/blob/a0b97b0c962de646f05f42f67ca7d53d630eb9ad/docs/design/2021-04-20-temporary-table.md) and see how it reflects in the tracking issue.

## Why not GitHub Project?

If you follow what GitHub provides to manage projects, you will be aware of [GitHub Project](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards) and possibly wonder why not just use GitHub Project.

Although changes to project boards are released along with the new GitHub Issue mentioned above, still I don't think it is a good idea to use GitHub Project, at least as a replacement for tracking issues.

The point is that GitHub Project is for management and provides a manager view, but open-source software development is not all of the management but almost of communication. You cannot comment on the project board and that ruins any other functions it provides.

If you are a group manager or feature owner, feel free to use GitHub Project as your personal board, but never regard it as a tracking issue. Contributors cannot comment on the project board so it is read-only. Also, its maintenance is out of the developer workflow.

Moreover, it is allowed to push issues, pull requests, or even arbitrary text cards in project boards. So what do you actually want to track?

## Epilogue

The Rust community adopts tracking issues and RFCs to track all substantial development among the community, which forms a nice workflow to merge significant contributions.

As an open-source developer in the TiDB community, I have proposed and been working to adopt tracking issues and design documents widely in the community. [Support temporary table](https://github.com/pingcap/tidb/issues/24169) is a good case except it tracks mainly pull requests instead of subtask issues. Further development will use and improve this best practice to track our open source development clearly, participant friendly, and recognizably.
