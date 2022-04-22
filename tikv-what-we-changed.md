---
title: 'TiKV: What We Changed'
date: 2021-07-31 10:41:47
tags:
    - Open Source Program Office
---

TiKV has undergone a governance reorganization during the last two months. It started from [Proposal: Reduce the Entropy of TiKV Community Governance](https://github.com/tikv/community/issues/118) and ended with permission reorganization, authentication mechanism updated, and governance description rephrased.

In this article, I'll show you the problem our community met, the solution we concluded, and the rationale behind the actions.

<!-- more -->

# What is the problem our community meets?

Every project has its effective governance. As the project grows, explicit governance helps new contributors on board and ensures decision-making clearly and properly.

When the proposal was put forward, TiKV adopted a governance structure inherited from the Kubernetes community, which consists of special interest groups and working groups. However, this model has been proven inappropriate for the TiKV community, at least in the way the TiKV community applied it.

## Repositories

The first problem is that we didn't apply it to the whole community.

> Most of our repositories have no clear owners; for example, it is hard to say who has review or commit permission of [mur3](https://github.com/tikv/mur3) by our governance and community information.

Actually, only [tikv](https://github.com/tikv/tikv) and [pd](https://github.com/tikv/pd) were managed - other repositories were ignored. It hurts that contributors working on other repositories like rust-prometheus have less visibility as a member of the whole TiKV community. Moreover, it confuses new contributors that who could merge or approve a specific pull request was decided by a complex mixture of membership file, bot internal logic, and GitHub settings, depending on which repository the pull request created.

## Special Interest Group

Impedance mismatch between SIG structure and how development is sorted in the real world is to be blamed.

> Special Interest Group benefits domain-specific discussion, but sucks when coupled with governance; for example, it is hard to say a contributor contributing to TiKV security belongs to which SIG.
> 
> We should decouple community governance from the enterprise organizational structure where SIG is born. Because the community governance reflects the community itself and the evolution. SIG Coprocessor exists because there is a component, not because there is a team inside a company working for it.

Besides, the constitution of SIG is ridiculous and no one obeys it.

1. Roles confusing. What's the difference between leader and co-leader? They are both maintainer-alike roles in other projects. What's the purpose of setting up an active contribution role? Why do you want to apply for a role that can be easily reflected by participation and associated with no permission?
2. Regularly meetup is proven cargo cult soon - there are not so many things to be discussed synchronously regularly.
3. The promotion rule is broken. "Effectively reviewing code over 200 lines of code", seriously?
4. Exit mechanism is vague like "inactive for a while" - what is "a while"? Also, you cannot declare emeritus by yourself.
5. Chinese only. So does the community exist in China only?

So, nobody took the constitution seriously and even core developers didn't ask for becoming a committer. Community members threw the governance away.

## Working Group

Working groups provide nothing but a lot of overhead maintaining materials.

Any feature must be developed by a real-world working group. Its members can already collaborate with GitHub issues and pull requests and communicate in any way they prefer. Why do you want a "formal" working group to benefit nothing but bring burdens?

# What We Changed

First of all, rest in peace, working groups.

The proposal build a relationship in contributors, teams, and repositories.

* A contributor can be in many teams.
* A team can have many repositories, and its reviewers and committers have corresponding permission on those repositories.
* Most repositories owned by exact one team, expect [rfcs](https://github.com/tikv/rfcs) shared by all teams, and [community](https://github.com/tikv/community) managed by all maintainers.

Let's understand the change by answering a series of questions.

## What is a team?

"Team" is a replacement of "SIG" just to void "new SIG" and "old SIG" since we are going to change the relationship between SIG and the repository. A team has its reviewers, committers, and maintainers.

## Where is the SIG?

You might regard teams as SIG combinations.

* TiKV team consists of SIG engine, coprocessor, and transaction.
* PD team consists of SIG scheduling.
* Raft team consists of SIG raft.
* Prometheus team respects contributors working on rust-prometheus independently.

## Why not leave just one SIG TiKV?

There is a TiKV team after this proposal is applied, while we also have the PD team and the Raft team. Hadoop, ZooKeeper, and Ratis are different projects and I think it is similar to TiKV, PD, and Raft.

## Why not break down the SIG?

I do agree theoretically it is possible to maintain `OWNERS` files to keep community governance reflect the software structure in fine-grained. But it costs too much and I don't think TiKV is gonna need it. We can use a simpler and permissive model in teams, to avoid the impedance mismatch problem. All TiKV reviewers and committers are equal to react to all events that happen in the repositories owned by the team. We do never separated ourselves unnecessarily, especially inside a repository.

## Why do you change roles?

* Reviewers and committers are translated unchanged.
* Leaders and co-leaders are translated to maintainers because these two roles have the same permissions, and we'd prefer more and more maintainers so it sounds a bit weird for many "leaders".
* Active contributors have gone because they can be easily reflected by participation and associated with no permission.

## Who has permission to review or commit a pull request?

A pull request is created on a repository. The repository is associated with a team. Thus, reviewers of the team can effectively review the pull request, and committers of the team can merge the pull request.

## What is the exit mechanism for team members?

Any team member is considered emeritus by their own declaration. An emeritus member is no longer participant in community affairs like decision-making or reviewing.

An emeritus member may request reinstatement, which will be sufficient to restore him or her to active member.

## What if a team member misuses his or her power?

Maintainers are able to call for a vote and remove his or her membership.

## How can I become a reviewer, committer, or maintainer?

In short, with a consensus of team maintainers. When a maintainer recognizes your contribution as significant as a reviewer, committer, or maintainer, he or she will nominate you as the role by calling for a vote to reach a consensus of team maintainers.

You can see [this voting thread](https://github.com/tikv/community/pull/137) as an example.

Note that we remove all former constitutions because they can hardly work. In community governance, it is important to distinguish requirements and guidelines. To promote a member, the requirement is the consensus. A team may have its own guideline to encourage contributors to focus on domain what they are looking for in membership, a team maintainer may share his or her own preference when nominating new members, but these are no requirements.

In this way, the community is more flexible to promote contributors and encourage further participation without being restricted by the outdated constitution. We never spend much effort creating rules only to break ourselves.

You can see the full content of [GOVERNANCE](https://github.com/tikv/community/blob/master/GOVERNANCE.md).

# What is the next?

Governance is only part of a community. We are working on the [TiKV Development Guide](https://internals.tidb.io/t/topic/277) for helping new contributors on board; we are bringing [TiKV v5.2 planning](https://internals.tidb.io/t/topic/235) for developing TiKV more publicly and releasing more predictably; we keep promoting well-qualified contributors to grow our community.

So, do not hesitate to join our community to enjoy the fun writing essential software, coding in Rust, and collaborating with excellent developers! You will be the next star of the community :)
