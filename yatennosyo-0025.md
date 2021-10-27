---
title: '夜天之书 #25 Evolving TiDB Governance'
---

今天接着聊上一篇 [Evolving Governance](yatennosyo-0018.md) 发出来以后收到的问题，即开源社区的治理模型应当因地制宜，这个结论是我在参与 TiDB 社区的时候观察得到的，上一篇文章只讲了原治理模型遇到的问题，但是经过修订后的 TiDB 社区的治理模型如何没有直接讨论。

本篇回答这个问题，即当前的 TiDB 社区治理模型是怎么样的，解决了哪些问题，还有哪些未来的工作。同样放一个事先说明，随着开源协同行业经验的积累和从业人员的成熟，最佳实践总是越来越好的。讨论过程中会涉及具体的开源社区案例，早期阶段的案例或多或少有不足之处，大多是时代所限，正是这些前人探索的实例，才构成了今天可以分析和演进的基础。

首先看到目前 TiDB 社区的治理模型图和原模型的介绍文章。

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

这里面 Maintainer 的角色除了有代码仓库写入权限以外，主要是做项目层面的决策，尤其是成员的引入和突出，也即对应了 TiDB 社区 Team 模型下的 Maintainer 角色。

Apache 项目采用了 Committer + Maintainer 的结构，其中 Maintainer 称为 PMC Member 并且有一些和基金会运行相关的细则。在 GitHub 上，不会有专门的 PMC Member 分组，而是统一用 committers 分组来为 Committers 和 PMC Member 授权。当然，在 ASF 的模型下 PMC Member 本身也是 Committer 的一员。

其中有些项目例如 Apache Curator 就在这个模型上实际执行了全员 PMC Member 的策略，没有是 Committer 而不是 PMC Member 的成员，即上面提到的合并也是可行的。也有些项目例如 Apache TVM 在这个模型上实际额外引入了 Reviewer 角色，类似于 Team 模型下的 Reviewer 角色。其他还有 Apache Hadoop 的 Branch Committer 角色，就不加展开了。

回到 Team 模型上来，Maintainer 角色定义改变是必然。先前模型的描述下，Maintainer 角色是游离于 SIG 模型的四层模型之外的。

> 重度参与 TiDB 社区的开发者，从 Committer 中诞生，对代码 repo 拥有写权限。

也就是 Maintainer 不在 SIG 模型里，没人能够提名和产生新的 Maintainer 成员，所以它实际并没有存在。只有这个模型推出时指定的几个人挂名，也从未以 Maintainer 的身份有什么活动。

所以 Team 模型的 Maintainer 角色某种意义上是取代了 (Co)Leader 的角色。这里有两点考量。

其之一是原先的 Leader 和 CoLeader 是个非常莫名的区分，没有任何的区别，也不需要 Maintainer 和 CoMaintainer 来对应。

其之二是用词区别下的角色定位的变化。我大概能理解 Leader 和 CoLeader 产生的缘由，即项目的 Leader 只有一个，其他同职责的成员就成为 CoLeader 以示区分。且不说实践当中有 SIG 直接就不管这些设定，而是直接在 Leader 栏写了几个人，凸显这个区分是个形式主义，单就假设 Leader 数量少到只有一个或几个人，就是开源社区运营上的一个误区。

Apache 项目在 PMC Member 当中有一名 PMC Chair 成员，但 TA 主要是向 ASF 董事会做汇报的，类似于项目在 ASF 当中的法人代表。与 SIG 模型下 (Co)Leader 对应的 PMC Member 角色可由多人组成，例如 Apache Hadoop PMC 有 121 人，Apache Flink PMC 也有 36 人。这是项目发展带来的必然结果。

如果把 Committer 排除在项目层面的决策之外，又仅有个位数的 (Co)Leader 支撑 SIG 的运转，是难以为继的。实际上，原模型发布之后曾经尝试持续组织双周会议就在一段时间后停滞。这里面有 SIG 切分粒度，可讨论事务的发现和具体技术运营的原因，也有组织者单点的原因。

Committer 是中流砥柱不需要动，Maintainer 是正名和扩张队伍。接下来再说 Active Contributor 和 Reviewer 这两个角色。

可以看到，在原模型的图示中，从 Active Contributor 到 Leader 是一个层级结构，而在新模型的图示中我刻意画成了并列结构。

这里的原因如同 [夜天之书 #8](yatennosyo-0008.md) 中所说

> Reviewer 和 Committer 的角色，不是社区当中的等级制度，而是一种信任的传递。社区的维护者赋予某位成员某个角色，不是升级或授予特权，而是基于信任简化社区参与的流程，同时鼓励这位成员进一步参与社区，发展社区，主持事务，自由发挥和自我实现。

从 Active Contributor 到 Leader 的层级结构，以及原模型中角色“晋升”的 PR 数要求等等，都会形成一种社区是一个打怪升级的环境的印象。当然，以游戏的方式参与社区也不坏，但是“等级”带来的不公平感却是有害的。

对于 Active Contributor 角色，上一篇文章评价如下

> Active Contributor 没有任何权限，而且很容易从 commit history 或者 GitHub 的 Contributor Insights 里看到，为啥要在章程里专门罗列这样的角色？

同时，在实践过程中，层级结构带来了等级观念。只是为了“晋升” Reviewer 而成为 Active Contributor 的情况是存在的，参与者在这里落入了形式主义的陷阱。实际上，根据个人的贡献，尤其在成员较少的社区，直接传递信任成为 Maintainer 的案例大有人在。至少一个人有资格成为 Reviewer / Committer 不需要一个 Active Contributor 的形式上的过渡阶段。

Active Contributor 是个事实，可以像 PG 社区一样展示 Major Contributor 列表，但不用刻意去“晋升”。

对于 Reviewer 角色，上一篇文章评价不多。除开层级结构的问题，再讲两个点。

第一个是强调 Reviewer 角色对社区参与的伤害。

任何人都可以参与开源软件社区 PR 的 Review 是一个共识，没见过禁止没挂角色的 Contributor 参与 Review 的情形。有这个共识在，去设置 Reviewer 角色就显得很奇怪。一个能够有效的 Approve PR 却不能够 Merge PR 的角色，强行解释是他们懂了一点，但没有完全懂，需要 Committer 来做最终判断。

这个说法乍一听是有道理的，但是其实 Reviewer 也能对某些 PR 是否可以 Merge 做出决定。这种现实的情况跟一刀切的模型是有出入的，极端的模型化思路甚至可以给 PR 评级，再给 Committer 评级，通过只能合并等级小于等于自己级别的 PR 来做到“完美”控制。开个玩笑，只是把设置 Reviewer 角色的思路推向极端。

PG 社区当中任何人都可以 Review 任何补丁，并且是点击 Become Reviewer 就能做到，哪怕你是刚注册到 PG 社区 Code Review 平台 CommitFest 的用户。这里的假设是 Review 是一个谁都可以做的贡献，社区欢迎任何人针对补丁提出意见。Committer 会最终把关并协助合并代码。不存在有人的 Review “有用”，有人的 Review “没用”的情形。

可能的争辩之一是没有这个意思，但是实际做了这样的事，势必会引起相对的反应。

可能的争辩之二是 Reviewer 降低获得角色的门槛及时反馈提高参与度，这在某些情况下不无道理，但是有两个问题。一个是确实社区中存在某些成员认为 Review 是 Reviewer 的工作或者才能做的工作，而实际上 Review Open PR 是参与社区的好方式，去告诉 Contributor 你可以 Review PR 是一件看起来很傻的事情，这会因为你设置了 Review 角色而成为一个问题。另一个是运行一个好的开源社区并不需要主动降低角色门槛来赢得新的成员，这个思路是一种取巧，另一个思路是优化达到 Committer 门槛路上的体验，在保持高要求的情况下吸引和留住成员。

发展一个 Committer 意味着非常高的信任程度，如果通过降低门槛来达到，最终会变成 Committer 自己大面积出现坏行为。中流砥柱腐化了，社区是无力维持的。

第二个是 Reviewer 角色定义背后对贡献认知的偏差。Reviewer 言下之意是 Review PR 的人，也就是把贡献等同于代码贡献。这对在社区当中宣导非代码贡献是有负面作用的。

最后，Reviewer 的定义很难跟 GitHub 的权限模型相结合。

总的来说，Community 当中的角色以信任传递为逻辑发展新成员，取得相应角色意味着能够基于信任简化社区参与的流程，利用权力进一步参与社区，发展社区，主持事务，自由发挥和自我实现。Community 不应当设置类别繁多的角色来形成层级模型或落入形式主义的窠臼。

Team 模型在这个原则下去掉了 Active Contributor 角色。对于 Reviewer 角色，直接去掉影响已经取得角色的社区成员的体验，于是折衷保留。

**Team 模型取代 SIG 模型，实质上是 SIG 模型演进为代码仓库粒度。**

Team 模型取代 SIG 模型，并不是重新发明一个全新的东西。社区治理总需要一个组织形式，叫它什么并不重要。SIG 模型和 Kubernetes 社区的 SIG 模型也不是一回事，有不少细微但是关键的差别。

模型之内角色的差别上面已经聊得很多了。从模型本身来看，两个模型的关键差别就是粒度的差别。为此在演进提案下专门有一个子任务叫

[Special Interest Groups should never divide repository](https://github.com/pingcap/community/issues/519)

TiDB 主仓库被几个 SIG 切分，由 labeler 打 SIG label 来限制权限，其中 labeler 只考虑了 sig-sql-infra / sig-planner / sig-exec / sig-migrate 这四个，对于其他 SIG 改动 TiDB 的需求尤其是原先事务相关的开发者是走 TiKV 社区的 sig-transaction 凭着两个社区共享 Infra 的假设和一些绕过机制的姿势来处理 Review / Merge 需求的。

这违背了两个原则之一的 GitHub 亲和性，同时理解谁能 Review 哪个 PR 以及谁能 Merge 哪个 PR 很反直觉，要人为说一段话解释。bot 的 comment 只会告诉你一个相关人员列表，但不会告诉你为啥。这个列表也是有问题的，这里就不展开了。

另一方面，分类的工作非常繁琐，labeler 在相当一部分情况下不能正确工作。上一篇文章讲过，Kubernetes 社区的 OWNERS 方案能运行是建立在良好的模块化上的，部分项目也没搞得那么复杂，整个项目根目录一个 OWNERS 文件了事。TiDB 的代码组织情况不足以支撑 OWNERS 方案的假设。

因此，新模型建立在代码仓库粒度上，只要你是 TiDB Team 的 Committer 之一，就能合并 TiDB 主仓库的代码。从此跟上面这些问题说再见。

**WG 模式消失。**

这个直接引用上一篇文章的介绍，形式主义且很久没人 follow 这个模式，直接移除。

> WG 也是从 Kubernetes 照搬的机制，原本的作用是通过社区的影响力和传播渠道对一些主题讨论或开发项目形成的工作组进行曝光和吸引参与，但是由于 TiDB 社区人力受限，并没有能力为 WG 提供此类帮助或其他帮助，实际上搞 WG 只是形式上要写一堆材料而已。很快，也就没人搞这个了。
> 
> 不过 WG 这个概念是客观存在的，软件开发很少是一个人的工作，而一群工作在相同模块，开发同一个功能的人总有某种办法相互联系，其实这就是 SIG 和 WG 的起源。不过要求 WG 写各种申请材料，Zoom 每周例会，做定期报告，就太傻了。

## 未来的工作

写到这里有点累了，未来的工作还有很多可做，这里只讲在社区治理上最重要的一点。

**治理模型和规则应该简单，但是社区运营的分享应该丰富。**

ASF 和 FSF 都有大量的文章阐述自己的历史沿革，创立理念和行事方式。Team 模型下新成员的发展在形式上是简单的，是一个提名和决议的过程。但是社区主观的寻找什么样的贡献者，认同什么样的开源协同理念，希望建设一个什么样的社区。这都是非常重要的。

对于每一个 Team 来说，只有说清楚自己在寻找什么样的人，并且通过描绘愿景吸引对应的人加入到自己的团队，才有可能真正建立起一个围绕核心理念打造核心价值的坚实的社区。

写不动了，先这样吧。
