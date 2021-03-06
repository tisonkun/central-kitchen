---
title: 在开源的世界里，应该公开地进行讨论
---

> 本文是对两个月前于个人英文博客发布的博文 TiDB: Why Forum? 的再发布。时隔两个月，重新审视这篇文章所讲的内容，其实立足于在开源的世界里，应该公开地进行讨论的原则上。同时，原文写成时所期待要做的后续工作也有了长足进展。本文主体仍然是原博文的内容，在最后增加对新标题的议论，以及对后续工作的进展同步更新。

[TiDB: Why Forum?](https://tisonkun.github.io/ziggurat/83dca9e786d4/)

TiDB Internals 开发者论坛于四月底上线，目的是提供一个讨论任何有关 TiDB 相关项目的设计与实现的平台。在这篇文章里，我们将讨论为什么开源社区应该有一个论坛，以及上述开发者论坛如今发展得怎么样了。

[TiDB Internals](https://internals.tidb.io/)

# 如何衡量社区的成熟度？

我们可以通过社区成员，参与度，治理形式，以及影响力等维度来衡量社区的成熟度。这里介绍一个来自 [ZoomQuiet](https://github.com/ZoomQuiet) 的社区成熟度模型。

* **L0** 无社区。大家不知道应该到哪儿讨论什么。
* **L1** 有社区。大家知道到哪儿可以进行讨论。
* **L2** 社区有规约。大家知道到哪儿应该讨论什么，否则有管理员出来纠正。
* **L3** 社区可自治。大家知道社区目标以及管理规约，并明确成为组织者的条件和路径。
* **L4** 社区自成长。社区变成大家日常生活习惯之一，并自学发掘或制造各种机会，关联各种资源，发展社区影响力。换句话说，社区归属感稳定。

大部分社区以 L4 形式启动，因为创始成员往往是一小群充满热情和信念的人，TiDB 也是如此。

TiDB 的创始人 [ngaut](https://github.com/ngaut)、[c4pt0r](https://github.com/c4pt0r) 和 [qiuyesuifeng](https://github.com/qiuyesuifeng) 都是充满热情和信念的开源软件开发者，早期就加入社区的成员 [siddontang](http://github.com/siddontang)、[shenli](https://github.com/shenli) 和 [disksing](https://github.com/disksing) 也是如此。

然而，随着社区的成长，一小群人的规模下通过多点过度讨论来同步的信息和项目目标，逐渐无法及时传递给新成员。核心成员非开发事务缠身，行为守则和最佳实践成为部落知识，社区瞬间回到 L0 的状态。

这就是今年四月底的时候 TiDB 社区的状态。项目托管在 GitHub 上，但是有些声音会说它仅仅开放了源代码。新成员不知道 TiDB 是如何开发的，因为 PR 突然地出现，蹦出来一群人 +1，又匆匆地合并，一切都以新成员看不懂的形式在进行。社区当中没有持久化地保存成员讨论内容的渠道，因此新成员很难参与到社区中来。

实话说，GitHub issue 和 PR 从形式上是持久化地保存成员讨论内容的渠道，TiDB 还有 Slack 频道。然而，GitHub 上的评论很少被响应，Slack 只能保存近几个月的聊天记录。

我作为 TiDB 社区的一员，在看到这样的情况的时候，第一件事就是期望把社区带回 L1 的状态，也就是大家知道到哪儿可以进行讨论。所以我着手建立了开发者论坛。

# 应该选择哪一种渠道？

L1 和 L0 的不同点在于大家知道到哪儿可以进行讨论，在上一段的最后我提到开发者论坛解决了这个问题。不过实际上，开发者论坛并不是唯一的解法。

在建立开发者论坛之前，我在已经存在的邮件列表里发布了一个[调查](https://lists.tidb.io/g/contributors/topic/survey_what_is_a_good/82016508)，题为“你认为什么是适合 TiDB 社区的讨论工具？”调查邮件把讨论工具分成了主题讨论和即时通信两类。

随后的讨论表明，即时通信可以暂不考虑，一方面是它的信息浓度太小，另一方面是开发者各有所爱，Slack 或者微信能够部分解决这个问题，但是都无法解决每一个人都知道到哪儿可以进行讨论的问题。因此，问题就变成了选择一个合适的公开进行主题讨论的渠道。

当时有这么几种可能的选项摆在我面前。

1. 从我参与 ASF 项目的经验来看，邮件列表可以工作得很好。
2. GitHub 的新功能 Discussion 看起来很酷，而且有好几个新潮项目已经开始用了。
3. Apache TVM 和 Rust 等著名的开源项目有自己的开发者论坛。
4. GitHub issue 或者其他 issue 追踪工具也是不错的候选。

## Issue

首先排除掉的选项是 issue 追踪工具。软件开发离不开 issue 追踪工具，但是它不适合开放式讨论。

Issue 总是绑定在某个代码仓库上的，并且通常围绕着一个确定且具体的主题。例如，报告一个缺陷或者记录一个具体的开发项。然而，开放式的技术讨论一开始往往非常模糊，不够具体。例如，粗略的功能设想，或者单纯展示一个小技巧。

Issue 的另一个不足是缺陷报告和各种开发项往往创建和更新频率非常高，这使得开放式的技术讨论经常被这些信息淹没。在处理具体问题是开发者往往有模式可寻甚至机械式地处理，而在进行开放式讨论时更关键的是创造性的思维和联想能力。

这不是说我们不用 issue 追踪工具了，恰恰相反，TiDB 的开发绝不可能离开 issue 追踪工具。然而，它不是我们回答到哪儿可以进行开放式的技术讨论的答案。

## 邮件列表

回过头来看，邮件列表、GitHub Discussion 和开发者论坛，都是很好的候选渠道。它们在发布一个主题和在专门的线程里进行主题化的讨论这一点上是一致的。只不过结果是开发者论坛更适合 TiDB 社区的情况。

从我参与 ASF 项目的经验来看，邮件列表可以工作得很好。[The Apache Way](https://www.apache.org/theapacheway/index.html) 强调了公开讨论的重要性，并要求所有交流都发生在邮件列表上。

TiDB 在当时已经有邮件列表了，而且我们甚至就是在邮件列表上做的调查，为什么不能就用邮件列表作为讨论的渠道呢？我把原因归结到文化差异和时过境迁上。

关于第一点，大部分 TiDB 的开发者并不成长于邮件列表在开源社区中扮演重要角色的年代。对于 Linux 和早期的 ASF 项目来说，邮件列表是最流行和有效的选择。相当多的 TiDB 开发者甚至不知道怎么订阅邮件列表，使用邮件列表进行讨论，等等。TiDB 的邮件列表在相当长的一段时间里并没有吸引到足够多的参与者，这也是我们无法把它简单的作为讨论工具的客观原因。不像 ASF 项目被规定要使用邮件列表，TiDB 的开发者有权选择自己的讨论工具，很显然，大部分人并不想用邮件列表。

关于第二点，不得不说人总是追逐新潮的东西。Rust 社区在 5 年前就停用了邮件列表，作为 ASF 项目的 Apache TVM 也将讨论的主战场迁移到了开发者论坛上，仅保留到邮件列表形式上的信息同步。必须承认，论坛对于下一代乃至当代的开发者来说，是一个更易于理解且更易用的讨论工具。

## GitHub Discussion

[GitHub Discussion](https://docs.github.com/en/discussions) 是 GitHub 为开源项目社区专门打造的协同交流论坛。

基本上，它跟一个论坛没什么两样。但是我们最终没有选择它，因为这个论坛必须绑定到一个代码仓库上。我当时说如果 TiDB 的项目组织形式跟 [CockroachDB](https://github.com/cockroachdb/cockroach/discussions) 相似，是一个中央大仓库的形式，那我们很有可能会采用 GitHub Discussion 作为无需运维的开箱即用方案。但很可惜，TiDB 社区不是这样的情况，它是由一系列代码仓库组成的。GitHub Discussion 绑定到一个仓库上无法适应 TiDB 社区的实际情况。

所以，我们选择开发者论坛实际上是通过排除法选出来的。在下一节里，我会讲讲开发者论坛如今发展到什么程度了，你可以从中看出这是不是一个合适的选择。

# 开发者论坛发展成什么样了？

原博文写成的时候，距离论坛建立大概过去了一个月，有超过 70 个注册用户和 10 篇热烈讨论的主题。到这篇博文发布的时候，已经有超过 160 个注册用户和近百篇主题发布。

当然，传统的运营指标并不是我们的目的，只是一个数字上的观感。我们的目标是建立起社区，让大家知道到哪儿可以进行讨论。甚至更进一步的，社区有规约。大家知道到哪儿应该讨论什么，否则有人出来纠正。

经过几个月发展，开发者论坛已经有比较好的目录切分，几乎每天都会有新的主题出现或者现有主题的回复。

原博文提到的 TiDB Development Guide 的提案，已经完成了前两个章节，并且在某些贡献者参与社区的过程中提供了可靠的内容支持。

原博文提到的 Rust 重写 PD 的提案，甚至近期已经由社区的核心开发者之一 BusyJay 开始动手实现原型。

关于技术的讨论和问答比比皆是。部分关键的开发活动，例如 TiDB 和 TiKV 的开发计划，以及社区决策，还有版本发布的信息也在论坛可以公开获知和讨论了。

如上所述，TiDB Internals 开发者论坛已经吸引了相当数量的开发者的参与，并且从中诞生了若干个具体的开发项，例如 TiDB 测试框架的迁移，BR 并入 TiDB 仓库等等。具体的开发项仍然会落实到 GitHub 上完成，但是早期的开放式讨论会发生在论坛上。

开发者论坛欢迎所有人讨论关于 TiDB 相关项目的设计和实现，开源协同的工作方式，以及有意思的点子等等。不过需要注意的是，开发者论坛不是一个支持团队，关于 TiDB 使用一类的用户问题解答，社区有专门的用户论坛 [AskTUG](http://asktug.com/) 来支持。

这里列举一些符合开发者论坛调性的主题，欢迎随时发起或加入讨论。

* 重构一段代码，例如查询优化器的实现，但是不确定重构的影响和需要保持的兼容性范围。
* 有一个初步的想法，需要听一听社区开发者们的意见，例如实现一个新的文件系统风格的存储引擎。
* 关于架构设计或代码实现的疑问，想要请教模块专家。
* 分享参与 TiDB 开发者社区的经验或最佳实践，亦或是对 TiDB 开发者社区的期待。

# 下一步要做什么？

随着 TiDB Internals 开发者论坛的发展，我们逐步把社区拽回了 L1 的情形，接下来要做的就是在社区建立规约和推动自治。规约不是凭空想象的，而是观察社区当前怎么运行的，因势利导总结出适合社区发展的一套原则。长远来说，最终希望把 TiDB 社区推到 L4 即社区自成长的阶段，助力 TiDB 社区的成员自我实现。

下面是原博文计划要做的工作，我会同步这些工作当前的进展。如果你对参与这些工作感兴趣，欢迎联系我。

## 开发者指南

也就是上面提到过的 TiDB Development Guide 的计划，这里的开发者指的是 TiDB 数据库的内核开发者。

这个计划最初由社区的技术领袖之一张建提出，全书分为四章。

* Get Started 介绍了准备环境，下载代码到开发一个补丁的全流程。
* Contribute to TiDB 首先介绍了社区指导原则，随后针对缺陷报告，功能开发和文档撰写等典型贡献流程做了细致的讲解。
* Understanding TiDB 是一个尚在撰写的章节，脱胎于源码阅读系列，旨在介绍 TiDB 各个模块的设计与实现。
* Project Management 则包括 TiDB 的开发活动组织形式和发布周期等项目关系相关的内容。

[TiDB Development Guide](https://pingcap.github.io/tidb-dev-guide/)

欢迎阅读开发者指南以参与 TiDB 社区。对于已经熟悉 TiDB 社区运行的同学，也不妨再读一遍换个视角观察。如果发现任何错漏，请不要吝啬提 issue 或者直接一个 PR 修复。

## 社区治理

如同今天在英文博客上发布的另一篇文章提到的一样，社区治理在 TiDB 社区是一个老大难的问题。关于这一点展开来说就太多了，我已经在 TiKV 社区里落地了一个社区治理改革的项目，下来我会用中文再把它的始末好好讲一遍。

## 发布

每一个 ASF 孵化器项目在毕业前都必须完成一系列符合 Apache 标准的发布，并证明发布流程可以被不同背景的维护者理解和重复。虽然这个过程有些古板，但是它确确实实能帮助社区理解开发节奏，发布周期，并有助于更好的社区协作。

TiDB 的发布在过去几年中大概维持了一年左右的发布周期，其发布流程之零散，除了极少数的发布大师根据一系列的部落知识能勉强完成发布，恐怕绝大部分项目的维护者都说不清楚 TiDB 是怎么发布的。

前面提到的开发者指南讲了关于发布周期的定义，开发者论坛逐渐会发布软件的开发计划并且同步版本发布信息。希望在不久的将来，任何人都可以按照确定的流程发布一个合格的 TiDB 版本。

## 测试框架

测试对于基础软件来说至关重要，MySQL 的成功离不开成千上万个测试用例。类似发布流程，如何撰写测试竟然也是一个部落知识。

开发者指南当中的 Get Started 一章唯一还没完成的一节就是关于如何撰写测试的。实际上，TiDB 的单元测试编写和调试复杂到我们宁可先做一轮框架迁移再来写这部分的指南。我发起的测试框架迁移提案已经吸引了十来个贡献者参与，期待你成为下一个参与者哦。

[Tracking issue for restructure tests](https://github.com/pingcap/tidb/issues/26022)

[如何参与改善 TiDB 代码质量？我是说...一分钟成为 TiDB 贡献者。](https://www.bilibili.com/video/BV1cM4y1T7D8)

当然，测试不仅仅是单元测试，下一步还有功能测试，场景测试等等能力需要服务化以支持任何社区成员能够贡献相应的测试用例。测试对于基础软件来说至关重要。

# 尾声

I believe TiDB community becomes a world class infrastructure community someday, and invite you to join this wonderful journey :-)

# 在开源的世界里，应该公开地进行讨论

这段内容节选自《制造开源软件》一书，原文已经足够好，因此只做搬运。

[Producing Open Source Software](https://producingoss.com/)

避免私下讨论

即使你已经将项目公开，你和你的创始人也会经常希望通过私下讨论来解决困难的问题。这在项目的开始阶段尤其明显，因为此时需要做出许多重要的决定，而只有少量志愿者能够胜任。你会发现公开讨论的明显缺点：邮件对话本身的延迟性，需要保留足够的时间来达成一致，处理自以为是的幼稚的志愿者（每个项目都有；有些将来会成为明星贡献者，而有些会永远保持幼稚），也就是那些不能理解你为什么只希望解决问题X，而X明显是大问题Y的子集的人。秘密决定并使之成为既成事实，或者至少成为联合和有影响力的投票集团的坚实推荐，确实非常有吸引力。

不要这样做。

尽管公开讨论可能很笨重，但是从长远来看这样做更合适。私下里做出重要的决定就像是将贡献者排斥出项目一样。没有重要的志愿者会愿意呆在这样一个由秘密委员会做重要决定的环境里。此外，公开讨论也会从其副作用中获益，无论是多么短暂的技术问题，一经发起都会一直讨论下去：

* 讨论有助于训练和教育新开发者。你不知道有多少双眼睛在关注着讨论；即使大多数人不会参与，仍然可能有很多人在静静的跟踪，收集软件的信息。
* 讨论会训练你如何向不熟悉软件的人们解释技术问题。这种技巧需要练习，你不能从已经知道你所知道的人那里获得这种练习。
* 之后，讨论和结论将会一直存放在公共归档中，可以保证以后的讨论不会回到同样的步骤中。见Chapter 6, 交流的the section called “归档的显著使用”。

最后，很有可能某个人会提出一个你从想到过的好主意，给对话带来真正的贡献。很难说这有多大的可能；这仅仅由代码的复杂程度和需求的专业程度决定。但是如果允许我使用轶事作为证据，我会证明这样做比直觉所期望的结果更好。在Subversion项目，我们（创始人）相信我们面对的是一组深入而复杂的问题，为此我们痛苦思考了几个月，我们很明确的怀疑在新建立的邮件列表中的会有任何人做出真正的贡献。所以我们选择了一条比较懒惰的方式，开始通过私下邮件讨论技术想法，直到项目的一个观察者[10]嗅出了问题，并要求将讨论公开。眨了眨眼我们这样做了—后来的结果让我们十分惊讶，我们很快便获得了许多有见地的回复和建议。大多数情况下人们提供的想法都是我们从来没有想到的。结果是邮件列表中一下子多了许多非常英明的人；他们只是在等待正确的诱饵。可以肯定地是公开讨论比私下讨论会保持更长的时间，也能得到更多的产出，花费额外的时间是值得的。

我们不必把问题总结为：“团结就是力量”（我们已经见过许多更成功的团队），但可以确认的是有一些事情适于在团队中完成。首先是有了大量的审阅；其次是快速产生大量的想法。想法的质量由其所针对的思想决定，当然，在你用挑战性的问题刺激他们之前，你无法判断这些思考者是那种人。

当然，也有许多讨论必须在私下进行，通过此书我们会看到这种例子。但是我们有一个指导原则如果没有保持秘密的原因，那就公开进行。

要想使之发生，我们需要行动。仅仅保证自己所有的通告公开是不够的。你也需要劝说其他人放弃不必要的私下讨论。如果某个人尝试开始没有必要的私下讨论，你要义不容辞的立刻进行恰当的元讨论。在你将讨论成功的引入公开场所之前，不要对原始主题做出任何回复，或者去确定私下进行是否必须。如果你一贯如此，人们会很快会意，并开始首选公开论坛进行讨论。
