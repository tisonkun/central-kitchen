---
title: '夜天之书 #20 The PostgreSQL Community'
---

今天对 PostgreSQL 的开发者社区做了一个概要式的分析，这里做一个总结。

PG 社区经过二十五年的发展，早已积累了海量的最佳实践，大多可以从 [PG 的维基页面](https://wiki.postgresql.org/wiki/Development_information)上找到。这篇文章不会覆盖所有内容，只做挑选分享，并强烈建议近期如雨后春笋般涌现的开源基础软件公司探索维基页面乃至协同编辑，学习这笔宝贵的财富。

## 社区组织

PG 社区的治理模型简单到我都不太能够称呼它为一个治理模型。

虽然它在全球地域性的协会组织不少，也有行为准则委员会等等组织形式，但是实际对 PG 的开发产生深远影响的是这样两个组织。

### Core Team

Core Team 是 PG 社区实质上的指导委员会。它负责代表项目做出决定和协调开发过程当中的冲突，能够做出 PG 社区所有问题的最终决定。

Core Team 一共只有 7 人，来自于 4 家公司，均在 PG 社区贡献了超过十年。最新的 2 名成员在去年底选出，原因是 EDB 收购 2ndQuadrant 后，原本的 5 名 Core Team 成员里有 3 名均来自同一家公司，打破了 Core Team 不该有一家公司有过半数名额的不成文共识。

官方网站的 [Contributor Profiles](https://www.postgresql.org/community/contributors) 页面罗列出了 Core Team 成员及其背景和贡献。此外，共有 5 名前 Core Team 成员已经退休。

Core Team 的主要职责包括

* 协调版本发布活动
* 充当保密沟通信道
* 发布政策变更公告
* 管理代码提交权限
* 处理行为规范问题
* 无法达成共识时，做出最终决定

可以看到，这个角色的职责描述是站在社区利益的角度上来讲的，成为 Core Team 成员并不意味着高人一等，而是有意愿帮助社区协调处理那些难以解决的非开发事务。这是一种贡献而非特权。这启发我们在构建开源社区的时候，定义角色时应该以社区价值为主，而非认为自己在树立特权阶级。社区当中针对某些事务做出最终决定的人，不是社区当中的特权阶级，而是通过信任的传递得到认可的个体。这点在 PG 社区有充分的体现。

PG 社区尤其强调 Core Team 成员应当避免直接决定技术方向和倡议，这些决定最好由公开讨论得出结论，例如在邮件列表上讨论。

新的 Core Team 的成员由当前的 Core Team 任命，过程不公开，仅公示结果。

关于 Core Team 组织形式的补充讨论，可以阅读下面这篇博文。

[Is it time to modernize the processes, structure and governance of the PostgreSQL Core Team?](https://postgresql.fund/blog/is-it-time-to-modernize-postgresql-core/)

### Committers

如同其他开源社区一样，PG 也定义了能够直接向主仓库提交代码的角色。

略有不同的是，其他社区往往会显著的展示 Committers 名单列表，例如

* [Apache Flink Committers](https://flink.apache.org/community.html#people)
* [Apache Curator Committers](https://curator.apache.org/team.html)
* [Python Committers](https://devguide.python.org/developers/)

PG 社区的 Committers 页面比较朴素，而且由于维基页面缺少索引，比较难找。而且在官方主页上也没有发现任何链接跳转到这个页面。

[Committers](https://wiki.postgresql.org/wiki/Committers)

一共有 28 名成员，对于一个发展了 25 年的社区来说，这个数量算是非常稀少了。

这个名单里仅有 5 名 Core Team 的成员，也就是说有 2 名 Core Team 成员并不在 Committers 队伍里。其中一人致力于社区发展和网站建设，另一人开发了 pgAdmin 工具，开发和维护 PG 社区大量的基础设施，并维护 PG 的安装体验。

同样，这可以看出 PG 社区的 Committers 也是认可和责任胜过特权和等级。后面介绍典型的开发流程的时候，也会看到 PG 社区的 Committers 承担了非常多的责任。关注在其他活动上的 Core Team 成员不想或无力承担 Committers 的职责，于是选择不成为 Committers 的一员。

这是关注在能力和职责而非形式主义的最佳实践。Python 社区也有一部分开发者收到邀请后拒绝成为 Committers 以保持自己业余参与的从容。相比起这股开源之风带起的追名逐利者恨不得给自己安排上更多更响亮的头衔，成熟开源社区的参与风格关注的是项目的成长和自己力所能及的贡献。这其实是 PG 社区少规则，多最佳实践，依靠小团队高度互信运转的基石。

新的 Committers 通常在每年三四月份由 Core Team 选出，并在 PGCon 上宣布，选取过程不公开。淡出社区的 Committers 将会同期被 Core Team 评估后移除 Committers 队伍。

维基页面上描述了选拔 Committers 的一系列宽松共识

* 多年来对 PG 项目做出了重大贡献。
* 一系列持续的代码贡献。
* 愿意承担一个或多个领域的维护工作。
* 主持 Review 进程，帮助其他贡献者提交补丁。
* 其代码贡献一贯是高质量的，不太需要修订或更正。
* 深刻理解接受一个补丁的流程和标准。

此外，在组织形式上，除了前面提到的全球地域性的协会组织，和行为准则委员会以外，值得一提的是 PG 社区的运作实体是一个叫 [PostgreSQL Community Association of Canada](https://www.postgres.ca/) 的非盈利组织。其董事会成员共 6 人。

* 1 人为非 Contributor 的财务官。
* 3 人为 Core Team 成员。
* 1 人为前 Core Team 成员。
* 1 人为茫茫多 PG Contributor 的一员。

这个组织和前面两个组织也没有包含关系。

真的 PG 社区是有高度的凝聚力和相互新人，以至于它们能够让愿意担责的合适的人出现在对应的位置上，而不用费尽心机地考虑其他背景的贡献者是否可靠，需要怎样保证社区在“控制”之下等等问题。

## 开发流程

### Bug

### Brand new features

### CommitFest

### Release

## QuickStart

## 总结




Kubernetes 把社区玩成了一个游戏，PG 把社区玩成了一个精英俱乐部，沙龙。
