---
title: '夜天之书 #27 Technical Domination'
---

上周末的中国开源年会上我做了一个[《Why Contributors Stay and Grow》](https://www.bilibili.com/video/BV1Tg411K7KS/)的分享，最近会把其中的各个小点分开来以文字形式展开讨论。

今天要讲的是众多新兴的开源社区的维护者关心的一个问题，即如何激励 contributor 参与乃至持续的参与到开源社区当中来。这个问题的切入点很多，但是有一个最关键的手段或者说是前提条件，就是要保持开源社区核心的开源软件的技术竞争力。

我们先看几个项目的例子。

* [Timely Dataflow](https://github.com/TimelyDataflow/timely-dataflow) and [Differential Dataflow](https://github.com/TimelyDataflow/differential-dataflow)
* [Apache Spark](https://github.com/apache/spark)
* [Delta Lake](https://github.com/delta-io/delta)
* [Materialize](https://github.com/MaterializeInc/materialize)

它们的共同点是极强的技术竞争力天然地吸引了诸多开发者的关注和参与。

我不会详细分析它们的项目形态和社区组织，但是在共同点之下项目的开源模式大不相同却值得聊聊。

Timely Dataflow 和 Differential Dataflow 发源自流式计算经典的 [Naiad](https://sigops.org/s/conferences/sosp/2013/papers/p439-murray.pdf) 论文，项目的发起人和核心维护者 [Frank McSherry](https://github.com/frankmcsherry) 是论文的作者之一。这个项目是纯粹的开源项目，以 MIT License 许可。

Apache Spark 耳熟能详了。这是在 Apache Software Foundation 下的开源项目，以 Apache License 2.0 许可。但是，和 Timely Dataflow 不同，它的开发和维护很大程度上受到 Databricks 公司的影响。不过 Databricks 公司以外的力量不容小觑，开发的流程大体上还是良好的遵守了开源协同的共识。

Delta Lake 是 Databricks 公司为 Spark 开发的存储层，与 Spark 一起形成了数据湖解决方案。这是在 Linux Foundation 下的开源项目，以 Apache License 2.0 许可。显然，这个项目很大程度上也受到 Databricks 公司的影响。更进一步的是，在 Delta Lake 的社区当中直接区分了来自 Databricks 公司的提交和来自公司以外的提交。前者的提交信息会包括指向闭源的 issue tracker 的编号，后者会确保提交信息中包含 sign-off 以满足 DCO 的要求，同时首次提交 contribution 还会要求签署一份 Databricks 的 iCLA 协议。

Materialize 是上面提到的 Frank McSherry 联合创办的 MaterializeInc 公司开发的流式数据库项目。这是一个源码可得的项目，以 [Business Source License](https://mariadb.com/bsl11/) 许可。简单说明，这个协议由 MariaDB 公司起草，主要内容是源码可得，使用分发有类似专有软件的限制，例如不可以部署集群，不可以商用等等。同时，会有一个条款说明这个协议许可的内容在一个时间点以后将以另一个开源协议许可。一句话总结，现在是专有软件，几年后变成开源软件。

可以看到，这个顺序是从彻底的开源项目逐步走到源码可得的专有软件的。但是这些项目都得到了不小的关注，并且能够吸引到开发者参与开发。这是因为它们在细分领域上都有明显的领先优势甚至就是绝对的王者。

从技术竞争力的角度对比着来看，Timely Dataflow 对应的是 Apache ZooKeeper 等项目。同样是彻底的开源项目，Apache ZooKeeper 显然不受任何一家公司所主导。当初大行其道的时候社区也是尽显繁荣。然而时至今日，因为软件质量以及紧随而来的跟不上时代的需求，Apache ZooKeeper 的技术生命已经到头，社区也就相应的凋敝。我曾经开玩笑说要想救 Apache ZooKeeper 只能是发 4.0 版本，但是维护者和用户都不希望也不需要一个 4.0 版本，所以就让这个项目在岁月中死去吧。

Apache Spark 虽然经受着新秀的冲击，但是其在分布式数据处理引擎的王者地位却从未动摇，甚至在去年发布了 3.0 版本，和 Delta Lake 构成的解决方案生态一起焕发新春。与之相对应的可以是 Apache Kafka 以及 Apache Flink 等项目，它们背后也有一家具有主导实力的公司的影子。但是在其基本目标实现之后逐渐失去了技术领导力。

Apache Kafka 虽然在两个月前发布了 3.0 版本，商业公司 Confluent 也上市成功，但是在消息平台领域被后起之秀 Apache Pulsar 不断冲击，ksqlDB 被 Materialize 迎头痛击。Kafka 社区正在逐渐失去活力。

Apache Flink 仍然是有状态流式计算的事实标准，但是基础的流式计算场景已经实现完毕，大部分功能处在追赶其他分布式系统的阶段，技术前沿没有提出新的愿景。流批一体倒是颇有进展，可惜这个方向还处于探索阶段，开发者对于流批一体是未来基本没有疑虑，但是是否当前应该参与进去，流批一体面临哪些挑战，如何逐步解决缺少明确的风向标。从而使得 Apache Flink 社区的技术主导力下降，核心成员转战 Snowflake 或 MaterializeInc 等公司，在破坏性变更不断出现的背景下迟迟无法发出 2.0 版本。

Delta Lake 对应的是某 IoT 大数据平台。后者在技术上的突破不足，未能吸引到足够多的资深开发者关注，在依赖公司内部的 issue tracker 记录问题的背景下，逐渐与公司以外的社区成员形成信息差。设计不公开，问题不清楚，参与门槛人为拔高，从而社区凋敝，只能采用赔钱赚吆喝的手段强行提高所谓的社区活跃度。其实质量很低，完全不是开源项目十倍于闭源生产力的水平。Delta Lake 多少也会有类似的问题，但是技术的领先以及对社区的及时响应，在公司之外也有关注参与到 Delta Lake 项目的资深开发者，设计讨论拉扯之下，更多的技术信息在社区当中流通，信息差较少，社区尚能运行。

Materialize 就不对应了，作为一个闭源软件，参与就是给你的公司白打工。除非产品变好能改善生活，即我本来就在用你的产品，或者纯粹提高个人技能，是不会参与的。Materialize 自然也很难吸引到资深开发者，但是它的技术是行业领先的，关注并且没有竞争关系的开发者也不会吝啬为其提交代码。毕竟社区里有高手，交流代码和软件设计心得，响应又及时，就是社区本身提供的价值了。

**开源社区的运行对维护者包括技术水平在内的多方面能力都提出了挑战。大体上，对于一个维护者来说，你需要释放出两倍的生产力，再付出一倍的精力，才能撬动社区协同模式十倍的生产力。社区不会自动地运行，始终需要 Critical Mass 指引方向和全力投入。**

总的来说，类似我在《Why Contributors Stay and Grow》主题演进里提到的动机，以及上周末在某个闭门会上讨论 contributor 激励时的观点，开源社区始终是围绕着人和开源软件展开的，两者缺一不可。激励的根本就是给予人的连接以及软件的发展正向激励。

真正想要运营好一个开源开发者社区，最根本的问题是社区核心的开源软件是否有强大的技术主导力，开源社区的愿景能否吸引资深开发者的投入。例如 GNU 运动想要替换掉一整套专有操作系统技术栈，Apache Pulsar 想要做消息平台的最终解决方案，PostgreSQL 始终称自己为世界最先进的开源数据库。诸如此类，才能找来最有价值的参与者。

主题演讲里对 contributor 动机做了分类，其中的自我驱动和认同归属就是上面提到的这种状态。当然被技术吸引的是一部分，被开源理念吸引的是一部分，通过人的连接建立起归属的也是一部分。

退而求其次，就是组织驱动，即组织的存续或价值创造依赖于开源项目，于是通过绩效评估等手段驱使其成员投入开源项目。但是，仅有此动机的成员会在离开组织或组织变动时离开开源社区。

再次就是通过直接物质激励“拉新”，例子这里就不举了。我认为这种手段仍然是有效的补充，但是类似消费者运营的手段“拉”来的新人如何进一步参与到社区当中，持续创造价值，就是一个全新的问题了。当然，“拉新”一次性参与，解决 good first issue 也是应当感谢的贡献。

最后，上面没有展开的商业公司与开源项目的关系的话题，我在新计划 FLOSSWAY 上有单独的讨论主题。

[The relationship between community and company](https://github.com/flossway/flossway/discussions/2)

FLOSSWAY 目前还有另一个开源项目采用 CLA/DCO 相关的主题。

[CLA or DCO for an open-source software](https://github.com/flossway/flossway/discussions/4)

FLOSSWAY 计划主要回答如何运行一个开源社区的问题，包括

* 如何处理开发者关系？
* 如何处理商业公司与开源项目的关系？
* 如何衡量评价开源社区？

比起方法论和道理，FLOSSWAY 更加重视运行开源社区的手段、技能和案例分析。

欢迎关注！
