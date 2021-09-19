---
title: '夜天之书 #17 Drive Cooperation'
---

这几天读完了 ZeroMQ 的社区建设实践，预计将在近期做一个分享，交付上借书的好兄弟的需求。

今天讲一讲社区当中引领潮流的先锋队驱动开源协同的几个点，也算呼应[《ZeroMQ 社区》](https://zguide.zeromq.org/docs/chapter6/)一章列举成功样例的模式。

**社区的先锋队是贡献者技术领袖和意见领袖，他们是动员社区力量的中枢。**

社区的先锋队是贡献者当中的灯塔。他们在社区当中讨论演进方向，设计开发代码，分享工程实践，树立行为标准。

我从开源社区中学习到一个经验是，必须自己坚信想要推动的议题的目标和价值。只有这样，你的行为和判断标准才不会偏离目标，才能带动别人。这是方向性问题。

大部分贡献者会跟随社区当中的技术领袖前进，技术领袖需要对方向有信心，能够解答或者致力于解答过程当中的问题。进而，驱动协同的力量往预期的方向努力。

例如，曾经在 Apache Flink 社区有过一次对 [Client API 的大讨论](https://lists.apache.org/thread.html/ce99cba4a10b9dc40eb729d39910f315ae41d80ec74f09a356c73938%40%3Cdev.flink.apache.org%3E)。我和 Kostas Kloudas 以及 Aljoscha Krettek 在其中针对作业提交的方式和抽象，以及 user-facing API 的设计做了全面的了解，解答了不同贡献者提出的问题，最终落实了多个提案和改进工作。

* [FLIP-73: Introducing Executors for Job Submission](https://cwiki.apache.org/confluence/display/FLINK/FLIP-73%3A+Introducing+Executors+for+job+submission)
* [FLIP-74: Flink JobClient API](https://cwiki.apache.org/confluence/display/FLINK/FLIP-74%3A+Flink+JobClient+API)
* [FLIP-85: Flink Application Mode](https://cwiki.apache.org/confluence/display/FLINK/FLIP-85+Flink+Application+Mode)
* [FLINK-13713: Remove legacy Program interface](https://issues.apache.org/jira/browse/FLINK-13713)

其他 FLIP 的过程大同小异，例如 FLIP-6 和 FLIP-27 等，都是由先锋队驱动开源协同，动员社区力量完成整个提案落地的经典案例。

又例如，TiDB 社区的 [Temporary Table](https://github.com/pingcap/tidb/issues/24169) 功能和 [Placement Rules in SQL](https://github.com/pingcap/tidb/issues/18030) 功能在 @djshow832 @tiancaiamao @morgo 等 Committer 的带领下，前后吸引了多位贡献者参与一同实现，完成了实现新功能，新功能跟现有功能协调，以及功能测试等等工作。

再例如，[TiDB 单元测试框架迁移](https://internals.tidb.io/t/topic/200)的工作中，我先提出迁移方案的草案，随后解答了对于方案目标和实现步骤以及细节的种种疑问，促使方案顺利通过。目前，这个提案已经吸引了不少于 30 位贡献者的参与，以意想不到的速度解决 TiDB 社区若干个 Go 项目对年久失修的单元测试框架的不良依赖。

上面的例子包括了功能开发或改进和代码重构及迁移等工作。这些工作在特定的程序员眼里可能会有“鄙视链”，进而在潜意识中引起社区贡献“偏科”，最终导致开源项目崩盘。

为了避免最坏情况，同样需要先锋队坚守软件工程的最佳实践并提供大体正确的指导意见。如果先锋队方向错误，且无力纠正，或者社区中的能人异士取而代之，或者自由派生出新的社区，或者社区就此凋亡。

**针对“鄙视链”这个情况需要先锋队做的事情是，传播客观的价值判断，找到不同工作给相应的贡献者的价值。**

对于纯粹想混个贡献者头衔的人来说，提供 good first issue 给他。例如前文测试迁移的工作中，有相当部分的工作是较为机械的。这些工作可以交给此类贡献者来完成，告诉他们如何按部就班的完成一个贡献，得到贡献者头衔。

对于想要了解某一个模块的贡献者来说，告诉他这块代码的设计方式，以及在这个模块上曾经集思广益想过但没有实现的想法。例如一个想要了解 online ddl 的贡献者，完全有可能自测试迁移出发，从测试视角了解函数和功能被使用的情况，进而了解测试的设计思路，评估并实现过去想做而没做的方案，最终了解整个模块的逻辑并提出自己的重构意见或功能提案。

其他类型的贡献者不一而足，例如主要需求是社区影响力的贡献者，关注软件质量的贡献者，喜欢撰写文档的贡献者，先锋队需要做的是描绘一个满足他们想要价值的路线，分别因势利导到相应的位置和工作上。这样才是开源协同提高软件开发效率的方式。

软件开发关注的对象包括人和工作，给定一项工作，找到有能力有意愿完成它的人，给定一个贡献者，找到适合他的工作，这是社区利用其基数大的优势创造价值的手段。

一种常见的错误实践是，同时给定工作和人，强行撮合这个人去完成相应的工作，往往还会匆匆地宣传和夸大这个案例，以造就一种虚假的繁荣。这是不可持续的。

另一个常见的错误实践是，不能应对 unqualified 的贡献者。对于比较复杂的贡献，先锋队可以根据自己的时间适当予以指导，在不能胜任的情况下也需要及时劝退水平还欠火候的贡献者，引导到其他低门槛的工作当中。同时，协同工作中往往并不能完美的切分，有些关键路径上的 blocker 也需要先锋队付出相应的努力去清除。

**最后，平时应当保持和社区成员的联络，这样才能够知道谁是上面所说的哪一种角色。**
