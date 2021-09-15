---
title: '夜天之书 #15 Public Design'
---

今天要讲的开源协同议题是 Public Design 公开设计。

开源协同的重要组成部分是开源软件的项目管理。某种程度上，开源社区的运营就是调动贡献者的积极性，并协调开发工作往同一个方向上走。如果有项目路线图，那就是路线图上的方向。

国外常用 Herding Cats 来形容项目管理，在开源软件上的协同对“牧猫人”的要求还会再高一些。因为现在他们要在充满多样性的社区当中，与不同背景的开发者合作来开发软件并保证软件质量。

Public Design 是开源软件开发的一个重要组成部分，即开源软件的功能开发和重要更改需要基于公开的技术设计在社区当中通过讨论达成一致以后才开始实现。

这在不少开源项目当中是不言自明的。例如 Python 社区有著名的 [PEP 流程](https://www.python.org/dev/peps/pep-0001/)，所有重要改动都可以在此追溯到。这种模式往上可以追溯到 RFC 的年代，贡献者们提出议案，寻求评论意见，在开源社区当中达成共识以后开始实现。

不过，对于年轻的开源社区来说，尤其是同一背景的开发者占优的社区，这个公开设计的过程可能会变成私下讨论或者小部分人设计以后就拍板实现。甚至在开源社区当中，只能看到突然出现的代码变更，而无法把握软件演进的背景和方向，也就是看不到软件开发的全貌。

不要这样做。

开源软件可靠的一个重要表现就是，可以追溯需求的来源和背景，社区的共识，以及功能实现的过程，可以支撑相关过程记录与还原。

如果开源软件的技术设计是私下讨论的结果，软件演进的方向是部落知识，那么有进取心的贡献者会因为无法得到足够的信息而受挫，富有经验的开发者会因为不信任感而离开社区。

TiDB 和 TiKV 社区当中不乏这样的例子。

* [Raft Async IO](https://github.com/tikv/tikv/issues/10540)
* [Cardinality Estimation Enhancement](https://github.com/pingcap/tidb/issues/26085)
* [SPM Enhancement](https://github.com/pingcap/tidb/issues/25970)

上面的三个功能，并不是没有设计，而是只在小范围内通过中文文档做出设计，就开始实现。

甚至在 Cardinality Estimation Enhancement 的例子当中，贡献者想了解功能设计和背景，被开发者以时间紧迫为由回绝。这是一个非常恶劣的反面例子，因为它将一个潜在的主动的贡献者拦在门外，并将在社交网络当中带来持续的负面影响。

哪怕是 Spark 或 Flink 这种有影响力强大的公司参与的社区，功能的开发也是公开透明的。即使在开发上时间紧迫，设计依然是公开的，流程上没有特例。同时，公开的设计思路和潜在的讨论鼓励贡献者通过 Review 或 Testing 等多种方式参与功能的开发和验收。

我们无法保证如果做了 Public Design 就一定能在短期内得到回应，但是可以肯定的是好的 Public Design 将对软件开发带来深远的影响。

另一方面，如果这个过程是秘密进行的，那么贡献者参与的概率，哪怕拉长到几年，也将是零。

当然，TiDB 和 TiKV 社区当中也有好的例子。例如 TiDB Committer Morgan Tocker 在做功能的时候就有好的设计和讨论的过程。

* [Defining placement rules in SQL](https://github.com/pingcap/tidb/blob/master/docs/design/2020-06-24-placement-rules-in-sql.md)
* [Dynamic Privileges](https://github.com/pingcap/tidb/blob/master/docs/design/2021-03-09-dynamic-privileges.md)

事实证明，这些设计在后来撰写 TiDB Dev Guide 和其他讨论场合当中也被引用。

Public Design 避免了信息变更以后需要口口相传新知识，并且可能在各个环节出现不同程度的落后的情形，让所有关注者共同编辑并且对齐同一份材料，是开源协同带来的信息传递复杂度的净胜。

为了做好 Public Design 并提供贡献者可以参考的样例，我在 TiDB 的开发者论坛 [internals.tidb.io](https://internals.tidb.io/) 上发布了一个讨论帖。帖子介绍了 Public Design 的提议背景，TiDB 和 TiKV 的设计实现流程，同时呼吁社区成员集思广益，推荐自己认为的最经典的设计文档。

[Discuss: Public Design](https://internals.tidb.io/t/topic/399)

目前已经收到了六篇提名，包括 TiDB 自己有过好的设计，也包括了 Apache Flink 和 Apache SkyWalking 的经典设计文档。欢迎大家了解和提名自己认为的好的设计文档。

为了收敛主题，我们关注在基础软件，主要是数据库、操作系统、编译器以及网络技术方面。

我们推崇谁，追随哪些先驱，决定了我们是谁。这也是开源社区 Public Design 的一个作用，能够展现社区的技术取向和追求。

最后在今天的议题之外，介绍一下最近在看的两份材料，可能随后会基于这些内容写后续的文章。

* [Contribute to TiDB](https://pingcap.github.io/tidb-dev-guide/contribute-to-tidb/introduction.html)
* [Collective Code Construction Contract](https://rfc.zeromq.org/spec/42/)
