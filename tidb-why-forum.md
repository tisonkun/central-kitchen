---
title: 'TiDB: Why Forum?'
date: 2021-05-22 22:57:34
tags:
    - Open Source Program Office
---

[TiDB Internals](https://internals.tidb.io/) developer discussion forum has built at the end of last month. It is the hub for discussing every related to the implementation and design of the TiDB projects. In this article, we are going to review the rationale of a forum on community, and how the forum grows so far.

<!-- more -->

> This is my first English blog. Do not hesitate comment or edit this page to correct writing mistakes.

# What is community maturity?

We can measure the maturity of a community by members, participation, governance, and influence. Here is a community maturity model for reference, by [ZoomQuiet](https://github.com/ZoomQuiet):

- L0: No community. Everybody has no idea what to discuss and where to discuss.
- L1: Community exists. Everybody knows where to discuss.
- L2: Community has principles. Members know what to discussion in the place, and maintainers ensure discussion follows principles.
- L3: Community is autonomy. Members understand the goals of community and follow code of conduct. Also there is clear community governance rules.
- L4: Community is self-improvement. Community affairs impact the day-to-day lives of members. Members have self engagement, share resources and opportunities, and spread community influence. In other words, members create their sense of belonging.

Most of open source communities start with L4 because members are a small group of passionate believers and so does TiDB.

TiDB is created by [ngaut](https://github.com/ngaut), [c4pt0r](https://github.com/c4pt0r), and [qiuyesuifeng](https://github.com/qiuyesuifeng). They are totally open source passionate developer, and so do other early members, such as [siddontang](http://github.com/siddontang), [shenli](https://github.com/shenli), and [disksing](https://github.com/disksing).

However, as community grows and core developers fall into non-programming activities, newcomers cannot catch the goals of community. Also principles and knowledge become tribal and never take effect properly any more. Even worse, the community is back to L0.

It was the situation of TiDB by the end of last month. The project is hosted on [GitHub](https://github.com/pingcap/tidb) but tends to be open source code only. Newcomers get confused by how the software is developed because commits are created but they don't know why. There is no channel for persistent discussion so one is even unable to participant easily.

To be honest, there are some channels such as GitHub [issues](https://github.com/pingcap/tidb/issues), [pull requests](https://github.com/pingcap/tidb/pulls) and [slack channels](https://slack.tidb.io/invite?team=tidb-community&channel=everyone&ref=pingcap-tidb). However, they are either rarely answered or unable to track full history.

As a member of TiDB community, in order to improve the situation, my first step to take the community back to L1, where everybody knows where to discuss. Here comes the forum.

# Which one to be chosen?

L1 is different from L0 by everybody knows where to discuss. At the end of last section it says here comes the forum; actually, it does _not_ have to be but the result.

At the first place a [survey](https://lists.tidb.io/g/contributors/topic/survey_what_is_a_good/82016508) on "what is a good communication tool for TiDB community?" was posted on the preexisting mailing list. The survey mail proposed two kinds of communication tools, one of which was for topic discussion and the other was for immediate messaging (IM).

It turns out that IM is unnecessary for the first place because message provides less information in IM situation. And also discussions are scattered because they are mixed in one channel. The community needs a topic discussion channel first.

I looked around to learn for existing best practices.

- Mailing list works well from my experience in ASF projects.
- GitHub Discussion looks cool and several open source projects already use it.
- Developer discussion forum is adopted by [Apache TVM](https://discuss.tvm.apache.org/c/development/5), [Rust](https://internals.rust-lang.org/), and others.
- GitHub issues or other issue tracking tools are always candidates.

## Issues

The first candidate to be excluded is issue tracking tools. We do need issue tracking, but not for open-ended topic discussion.

An issue binds to a repository and generally about a concrete topic; for example, reporting a bug or a specific development task. Many technical topics has unclear implementation at first, like rough feature ideas or showing off tricks. Another drawback is that issue tracking tools has high traffic especially of concrete tasks, and thus open-ended topic discussion is overwhelmed and can hardly attract attention.

It doesn't say we drop issue tracking tools. Issue tracking tools still play a significant role for collaborative development, but not the place for open-ended topic discussion.

## Mailing List

Mailing list, GitHub Discussion, and developer discussion forum, are all good candidates for TiDB community. They are nearly the same on posting a topic and discuss in the thread. However, developer discussion forum wins for TiDB community situation.

Mailing list comes as a candidate for my experience in ASF projects. [The Apache Way](https://www.apache.org/theapacheway/index.html) emphasizes open communication and requires all communications related to code and decision-making on mailing list.

Since TiDB has already a mailing list as we started the survey, why it cannot be the chosen communication tool? The result can attributed to culture gap and times has moved.

For the first part, TiDB developers did not grow in an age when mailing list acted as an important role of open source community like Linux or early ASF projects. They don't even know how to use a mailing list like its subscription and reply. TiDB mailing list attracts little audience and this is the direct cause we cannot make it _the_ communication tool. TiDB community has an opportunity to choose its own way and its members tend to reject mailing list.

For the second part, the Rust community stopped using a mailing list 5-ish years ago and Apache TVM uses a developer discussion forum although the discourse must be brought on-list. Forum is an easy-to-understand communication tools for the next generation of developers.

## GitHub Discussion

[GitHub Discussion](https://docs.github.com/en/discussions) is a collaborative communication forum for the community around an open source project provided by GitHub.

It acts almost the same as a forum while we don't choose it because it binds to a repository. If TiDB community is more like [CockroachDB](https://github.com/cockroachdb/cockroach/discussions) which has a central repository we might do it. But it is not the situation. TiDB community consists of a large range of projects includes [TiDB](https://github.com/pingcap/tidb), [TiKV](https://github.com/tikv/tikv), [PD](https://github.com/tikv/pd), [TiSpark](https://github.com/pingcap/tispark), [TiUP](https://github.com/pingcap/tiup), and so on. Binding to one repository is unacceptable.

So in fact, we choose developer discussion forum by elimination. In the next section, I'll show you how the forum grows and see whether it is a good choice really.

# How the forum grows?

So far, there are more than 100 developers active on [TiDB Internals](https://internals.tidb.io) and 10 topics are heated discussed.

[zz-jason](https://github.com/zz-jason) [created](https://internals.tidb.io/t/topic/46) a proposal of a GitBook for TiDB development guide. After a call for contributions stage, the working group [kicked off](https://internals.tidb.io/t/topic/94) and [started writing](https://github.com/zz-jason/tidb-dev-guide/commits/master).

[TennyZhuang](https://github.com/TennyZhuang) [suggested](https://internals.tidb.io/t/topic/72) an investigation of Rust implementation Placement Driver. PD developers show their interest and discuss about technical details.

[tison](https://github.com/tisonkun) [shared](https://internals.tidb.io/t/topic/84) the experience of building standalone TiKV Go Client, which engages [longfangsong](https://github.com/longfangsong) to [join the effort](https://github.com/pingcap/tidb/pull/24656).

[SchrodingerZhu](https://github.com/SchrodingerZhu) [asked](https://internals.tidb.io/t/topic/42) for suggestion on adding support of snmalloc to tikv_alloc.

As you can see, our forum has attracted a number of developers participation, and drives several concrete development tasks. Concrete development tasks still get done on GitHub, by issues that break down subtasks and pull requests that integrates patches.

You are encourage to discuss everything on the forum related to the implementation and design of the TiDB projects, but remember that TiDB Internals is **not a support forum**. Questions or requests for support using TiDB should be directed to the [user forum](http://asktug.com/).

Several sparks on what to discuss:

- if you want to refactor a piece of code, like the planner implementation, but unsure of its impact.
- if you have a rough feature ideas to collect feedback, like a filesystem style storage engine.
- if you would like to extract interfaces, like the scheduling strategy interface, and want to discuss with component experts.
- if you are gonna share the experience or best practice on developing TiDB projects.

Do not hesitate post a topic on [TiDB Internals](https://internals.tidb.io) and get replied.

# What is the next?

With the [TiDB Internals](https://internals.tidb.io/) developer discussion forum grows, we are dragging the community back to L1 maturity. The next steps would be towards community principles and guidelines for participation. For long-term goals, we are aimed at a community in L4 maturity which builds world class infrastructure technical influence.

Below are several insights of the next steps. [**Contact me**](mailto:wander4096@gmail.com) if you are interested in.

## Development Guide

In order to make code contribution, understanding how to develop TiDB projects is necessary.

We are working on [the TiDB development guide](https://github.com/zz-jason/tidb-dev-guide) now which focuses on the SQL layer a.k.a [pingcap/tidb](https://github.com/pingcap/tidb). It includes both "Contribute to TiDB" part and "Understanding TiDB" part. You can [click](https://zz-jason.gitbook.io/tidb-dev-guide/) to see a rendered version and send feedback or join the effort on the [repository](https://github.com/zz-jason/tidb-dev-guide) of the kick off [post](https://internals.tidb.io/t/topic/94).

## Community Governance

Community governance matters since it forms how to make decisions and how to be a reviewer, committer, or maintainer (abstractly, an option leader or organizer).

TiDB runs community governance with a large number of tribal knowledge which becomes entropy. I have written a [proposal](https://github.com/tikv/community/issues/118) to reduce the entropy of TiKV community governance at first and you can see "What is the problem our community meet?" as well as "What is proposed to do?".

## Release

Every ASF projects should make several [ASF releases](http://incubator.apache.org/policy/incubation.html#releases) before its graduation. Although a bit staid, it helps the community understand the development cycle and benefits better collaboration.

TiDB releases its software also with a large number of tribal knowledge that even its maintainers can hardly explain how it works. We are working at a clear and public release module and trying to share the RoadMap of TiDB so that everybody has an understanding of what they can contribute.

## Testing Framework

Testing is crucial for infrastructure software. Again, how to write a test for TiDB projects is tribal knowledge.

We plan to describe how to write and run tests with current codebase in the TiDB development guide. However, it is a long-term goal to build a concise and extensible testing framework.

## Standard Developing Procedure

This comes from an offline discussion with [c4pt0r](https://github.com/c4pt0r), and the name is inspired with "Standard Operating Procedure".

c4pt0r described a contributor journey that what if he wants to support a new SQL query syntax.

From a TiDB SQL layer expert's perspective, it mainly consists of changes on [pingcap/parser](http://github.com/pingcap/parser), the [planner](https://github.com/pingcap/tidb/blob/49f614e05f400c094a63a62de494f1bb640ce249/planner), and the [executor](https://github.com/pingcap/tidb/tree/49f614e05f400c094a63a62de494f1bb640ce249/executor). Also storage engine might be effected and some existing logics should be adjusted.

c4pt0r then asked how to bring this knowledge of expert to every passionate contributor, and even in details as well as standard.

My answer is that we are going to write down how to make several typical contributions in the TiDB development guide.

Also when we try to summary the procedures, we must find unreasonable code and logics in our current codebase. We do code refactor for better interface abstraction and components decoupling, and thus standard developing procedure can be self-described at a level.

Of course, in order to cover every specific developing procedure, the experts are suggested to share their knowledge publicly and participant developer discussion forum to give advise.

# Epilogue

I believe TiDB community becomes a world class infrastructure community someday, and invite you to join this wonderful journey :-)
