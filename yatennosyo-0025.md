---
title: '夜天之书 #25 Evolving TiDB Governance'
---

今天接着聊上一篇 [Evolving Governance](yatennosyo-0018.md) 发出来以后收到的问题，即开源社区的治理模型应当因地制宜，这个结论是我在参与 TiDB 社区的时候观察得到的，上一篇文章只讲了原治理模型遇到的问题，但是经过修订后的 TiDB 社区的治理模型如何没有直接讨论。

本篇回答这个问题，即当前的 TiDB 社区治理模型是怎么样的，解决了哪些问题，还有哪些未来的工作。

首先看到目前 TiDB 社区的治理模型图和上一篇介绍文章。

[新架构、新角色：TiDB Community Upgrade！](https://pingcap.com/zh/blog/tidb-community-upgrade)

![tidb-user-group](media/tidb-user-group.jpeg)

![tidb-developer-group](media/tidb-developer-group.jpeg)

Community 相关的材料可以在 [pingcap/community](https://github.com/pingcap/community) 仓库找到。

其中用户社区是上一篇介绍文章的重点之一，这点在本次演进中没有太大的变化。AskTUG 仍然是高质量的中文用户社区，TiDB 社区版主也是用户社区的中流砥柱。

[TiDB 社区版主，一群平凡又伟大的 TiDBer](https://asktug.com/t/topic/183426)

其中技术指导委员会（TOC）目前没有明显的活动痕迹，在本次演进中没有涉及，也略过不谈。

我们主要关注到 Team 模型上，介绍 Team 的结构，再讲一讲未来的工作。

## Team 模型与原理

一个 Team 拥有若干个 GitHub 代码仓库，存在 Reviewer / Committer / Maintainer 三种类型的成员。

* Committer 拥有代码仓库的写权限，是社区运行的中流砥柱。
* Maintainer 在此之上能够对 Team 层面的决策投有效票。
* Reviewer 没有写权限，但是 TA 对 PR 的 Approval 可以计入 PR 对 Review 数量的要求。

新成员由 Maintainer 提名及投票共识产生，没有其他的客观要求，包括原来的 PR 数量限制也不复存在。细则可以看 [Decision Making](https://github.com/pingcap/community/blob/33aca41f586b402b1eedb1526e923ac1cf3db90d/teams/README.md#decision-making) 文档。

TiDB 社区的 Team 一共有八个，简要介绍如下。

* **TiDB Team**: 维护 TiDB 主仓库及其依赖的卫星仓库。
* **Migration Team**: 维护 TiCDC 等 TiDB 数据库的中间件仓库。
* **Docs Team**: 维护 TiDB 相关项目和产品的文档仓库。
* **Kubernetes Team**: 维护 TiDB Operator 等与容器化相结合的仓库。
* **Diagnostic Team**: 维护 TiDB Dashboard 仓库。
* **TiUP Team**: 维护 TiUP 仓库。
* **BigData Team**: 维护 TiSpark 和 TiBigData 仓库。
* **PostgreSQL Team**: 维护 TiDB-for-PostgreSQL 及相关仓库。

大致由原先的 SIG 演进而来，其中 BigData Team 和 PostgreSQL Team 维护了 pingcap org 以外的仓库，这与 incubator 相关的话题有关，历史原因复杂，这里不做展开。

介绍完 Team 模型的内容，我们从演进提案出发聊聊形成这一结果的原理和权衡。

[Proposal: Lightweight and GitHub Friendly Special Interest Group](https://github.com/pingcap/community/issues/516)

演进方案如上，可以看到主要的设计原则是轻量级和 GitHub 亲和，后一点指的是 Team 模型和 GitHub 的权限模型没有明显的摩擦。我们从这两个原则出发来看前后两个模型之间的差异。

**Active Contributor 和 (Co)Leader 角色消失，Maintainer 角色定义改变。**

这是核心的变化，即角色的改变。

开源社区大多是从小长大的，对于一个起步阶段的社区来说，定义繁杂的角色只会滋生形式主义。角色的价值是与权力和责任挂钩，赋予信任且愿意处理相应事务的社区成员权力，帮助他们承担相应责任，从而推动社区的发展。

如果你的项目托管在 GitHub 上，GitHub 的模型定义了三层权限模型，随后扩展到五层。对于开源项目来说，只有 Write 和 Admin 是重要的，其中又以 Write 是最重要的。起步阶段的社区需要关注的是谁对代码仓库有写入权限，如何增加新的有写入权限的成员。通常来说，这会演化成 Committer + Maintainer 的结构，但是都合并成 Maintainer 也是可行的。



**Team 模型取代 SIG 模型，实质上是 SIG 模型演进为代码仓库粒度。**

**WG 模型消失。**

## 未来的工作

Where SIG goes and why?

Where WG goes?

Team 的 principle
公司与项目关系
