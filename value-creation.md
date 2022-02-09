---
title: '夜天之书 #41 共同创造价值'
---

如何吸引开源开发人员参与项目？如何让他们留下来，成为项目共同体的一部分？这是两个做开源运营必须回答的问题。

我对这两个问题的回答，简而言之是和开源参与者共同创造价值，使得开源项目和开源共同体能够回答潜在参与者的两个事关去留的灵魂提问。

1. 我能为你做什么？
2. 我应该怎么做到？

从共同创造价值的角度出发，通过开源运营回答参与者可以做什么的问题，只有可做的事情是令人兴奋的价值创造，才有可能触发潜在的参与者的兴趣。进一步，只有潜在的参与者能够在文档材料与其他成员的帮助下共同完成价值创造，这样的正向激励才能让参与者留下来，成为项目共同体的一部分。

本文内容部分整理自我在开源社举办的 COSCon'21 活动上的主题分享[《Why Contributors Stay and Grow》](https://www.bilibili.com/video/BV1Tg411K7KS/)的第二部分。

## 我能为你做什么？

考虑一个开源开发人员接触项目的典型旅程。他首先要知道这个项目的定位是什么，以决定是否进一步了解它。

如果项目的定位看起来很有趣，或者像是正在解决他希望解决的问题，那么进一步激发他参与贡献的诱因，就是他发现可以为这个项目做点什么。

如果这个项目复杂到无从下手，没有任何引导回答“我能为你做什么”这个问题的入口，那么大部分潜在的参与者都会选择直接放弃理解，也就无法参与。如果这个项目简单到不需要添加什么功能，例如 [LineNoise](https://github.com/antirez/linenoise) 和 [atoi-rs](https://github.com/pacman82/atoi-rs) 等等，或者稳定到没遇到任何迫切的新需求，例如 ZooKeeper 等等，那么大家已经用得特别开心，也就少有参与贡献的动机了。当然，后者或许是件好事。

我们考虑一个蓬勃发展当中的项目，它足够复杂以不断产生新需求，它又很有活力以致力于把问题解决得足够好。在这样的项目里，潜在的参与者通常能够为项目做什么呢？从这个角度出发，也就能够知道哪些是可能的动机触发点，以拓展共同创造价值的故事。

### 代码之内的参与

开源项目最终生产的是开源软件，很容易想到围绕软件代码参与贡献。典型的代码贡献可以分成这四类。

* 评审代码
* 修复缺陷
* 改进实现
* 增加功能

**首先要讲的是评审代码。**

这是一种经常被忽略的参与动机。因为相当部分开源共同体，总是考核并引导参与者自己写代码和提交补丁，只把写代码当成贡献，而将评审代码视作一种不得已而为之的成本，甚至当做是 committer 和 maintainer 的特权。

这当然都是不对的。

实际上，code review 是开源开发人员之间交流技术和建立信任的主要手段。大部分软件的生产过程中，解决问题的办法往往不止一种。每个项目会在众多可能性当中选择自己认可的技术实践，形成自己的调性。通过代码和文档，以及生产代码和文档的过程，这种调性以共识的形式从核心成员同步到每一个参与者的认知当中。这里所说的生产代码和文档的过程，code review 就是其中重要的一环。

对于潜在的参与者来说，参与代码评审并提出问题，门槛较之提交补丁整体要低一些。当然，评审代码并留下意见建议，很多时候要求 reviewer 对软件的理解比补丁作者本身要更高。然而，这里所说的参与代码评审并不局限于针对补丁的实现提出形如补丁的补丁的意见建议，而是强调围绕补丁代码观察和讨论本身。

例如，PostgreSQL 共同体的 [CommitFest](https://commitfest.postgresql.org/) 就允许任何参与者以 reviewer 的角色评审待合并的补丁。合并代码的动作自然只能由经验丰富的 committer 来执行，但是任何对这个补丁感兴趣的人，都可以参与评审。你可以针对实现提出问题，可以针对文档提出建议，可以本地测试补丁并回报结果，可以就自己不理解的地方，遵守[提问的礼仪](http://www.catb.org/~esr/faqs/smart-questions.html)提出问题。当然，如果某个补丁解决了你的问题，或者实现得非常精彩，不要吝啬感谢、赞扬和鼓励。

TiDB 开发者指南当中有专门的一个章节，告诉潜在的参与者他可以通过[评审代码](https://pingcap.github.io/tidb-dev-guide/contribute-to-tidb/review-a-pr.html)的方式为开源共同体做出贡献。其中关于撰写 review comments 的建议值得在这里分享。

* **Be respectful to pull request authors and other reviewers.** Code review is a part of your community activities. You should follow the community requirements.
* **Asking questions instead of making statements.** The wording of the review comments is very important. To provide review comments that are constructive rather than critical, you can try asking questions rather than making statements.
* **Offer sincere praise.** Good reviewers focus not only on what is wrong with the code but also on good practices in the code. As a reviewer, you are recommended to offer your encouragement and appreciation to the authors for their good practices in the code. In terms of mentoring, telling the authors what they did is right is even more valuable than telling them what they did is wrong.
* **Provide additional details and context of your review process.** Instead of simply "approving" the pull request. If your test the pull request, report the result and your test environment details. If you request changes, try to suggest how.

另外，代码评审并不局限于补丁合并之前，也不是必须发表评论。

如果一个已合并的补丁激起了你的好奇心，或者你发现了其中存在的问题，完全可以 review after commit 即合并后评审。这对于高速发展的项目来说尤其重要，因为它们往往会在较短的时间窗口内合并补丁，乃至直接向主分支推送代码。代码评审不是形式主义，不像某些极力推行某种流程的人所宣称的必须在合并前收集到两个赞同才能合并，务实的评审和合并策略应该是持续发生、交错进行的。

不是必须发表评论，意思是所有的参与者在提交代码之前，都应该了解他所要参与的这个开源共同体的惯例，也就是常说的“入乡随俗”。这个过程一般也是通过浏览现有补丁来完成的，其实也算是评审代码的一类。我在撰写提交信息和实际提交补丁之前，往往都会先观察共同体当中的其他人是怎么做的，避免不必要的摩擦，提高协同的效率。如果当前流程有明显的缺陷，也是一个潜在的参与点。

**修复缺陷、改进实现和增加功能，这三种都是代码贡献。**

理想情况下，潜在的参与者具备代码贡献所需的技术背景，在使用软件或阅读代码的过程中，自己发现可能的改进项，仿照现有的 pull request 风格提交补丁。

这种情况也不算少见。常见的案例是参与者掌握了一项新技能，例如一种新的代码风格或设计模式，一种项目管理或持续集成实践，或者一种具有一定普遍性的功能，从而把已经完成的工作，带到其他缺乏这个改进项的项目当中。具体的例子，比如我在看到我的工作里引用的 atoi-rs 项目，没有按照 Rust 项目的惯例配置支持的 Rust 版本，同时功能开发趋于稳定但却没有发布 1.0 版本导致我不是特别敢用，就通过 issue 和 pull request 的方式直接把我掌握的技能复刻到该项目当中。

* [Remaining works for 1.0 release](https://github.com/pacman82/atoi-rs/issues/14)
* [improve MSRV settings](https://github.com/pacman82/atoi-rs/pull/17)

上面的例子里有一点值得强调，就是当潜在的参与者不确定能够为开源项目做什么的时候，可以直接询问。当然，这种询问应该是有的放矢的，询问之前应该对项目做基本的了解，而不是居高临下的要求维护者准备好甚至生造出待完成的工作并交给自己。

反过来，从项目维护者的角度出发，回答代码贡献层面潜在的参与者可以做什么的问题，能够采取的方式包括以下几种。

第一种，也是 GitHub 原生支持和倡导的方式，就是为 issue 标注 good first issue 或 help wanted 标签。我在[夜天之书 #7](yatennosyo-0007.md) 一文里讨论过这两种标签的使用方式。绝大部分 GitHub 的用户的心智模型能够适配这两个标签，并且首先会尝试寻找 good first issue 或 help wanted 标签标注的 issue 作为参与的切入点。

第二种，以 tracking issue 的形式组织起待办事项。通过将零散的 issue 和 pull request 按照主题和模块组织起来，以类似于重构和组织代码的形式管理 issue 和 pull request 来降低潜在参与者的理解成本。

这种做法全面推行，就会在顶层形成一个项目的路线图。例如 [Flink 的路线图](https://flink.apache.org/roadmap.html)就把项目的模块分得比较清楚。每个模块现在是稳定状态，快速开发状态，还是原型状态也会标注出来。进一步的，列出每个模块当前正在进行的 Flink Improvement Proposal 和背景，开发人员就可以从这个入口了解相关工作，再从 proposal 关联的 tracking issue 参与到开发工作里面来。当然，这个过程里还有许多可以做代码之外的参与的切入点，这里不做展开。

路线图的更新频率比较慢，日常开发工作里接触得多的是 tracking issue 和对应的改进提案。成熟项目基本都会有一个完整的提案流程，从“我能为项目做什么”的角度出发，这个流程里包含的信息应该可以教会潜在的参与者分辨不同阶段的提案，并且理解当前阶段提案发起人需要得到哪些帮助。另一方面，关于 tracking 的组织，我做过一个视频[《如何在开源社区做项目管理？》](https://www.bilibili.com/video/BV1AV411W7WD/)具体讨论的实践手法。

这些手段的最终目的是一致的。因为开发活动过于琐碎，单个开发活动的价值很难吸引潜在的参与者付出时间和注意力自己补全所需的细节。这种情况下，作为项目维护者和开发活动的发起人，应该尽可能地从多个层面以人能理解的方式把这些具体的开发活动归纳总结，以提供不同详略程度的内容呈现。

如同前文提到的，这个过程类似于重构和组织代码。你不能指望开发人员一上来就盯着每一行代码看，这样低效率的理解项目的定位、设计和发展方向。同样，你也不能指望潜在的参与者从大量琐碎的开发活动里归纳出项目共同体正在做什么，接下来要干嘛。只有把开源项目的开发活动模块化和主题化，才有可能把理解和参与的门槛降低到当前时代下潜在参与者所愿意付出的精力的范围之内。

这其实不止是开源项目的问题，而是一个普遍的项目管理的问题。把潜在的参与者换成项目团队的萌新成员，推理过程和结论一样成立。项目维护者采取这样的做法，也不是全然无私奉献，而主要是控制软件工程由于复杂度增加带来的熵。这对于项目本身的健康快速发展也是有利的。

### 代码之外的参与

开源共同体虽然是围绕开源软件形成的，但是可能的参与形式远不止于代码贡献。[The Apache Way](https://www.apache.org/theapacheway/index.html) 经常被人引用的一点就是“共同体高于代码”。

> **Community Over Code:** the maxim "Community Over Code" is frequently reinforced throughout the Apache community, as the ASF asserts that a healthy community is a higher priority than good code. Strong communities can always rectify problems with their code, whereas an unhealthy community will likely struggle to maintain a codebase in a sustainable manner.

其实，这里的 community 是包括 code 的，两者并非互斥关系，只是强调决策的基点是共同体的利益，而不只是关注代码。不过，我们首先看到开源共同体当中代码之外的参与形式。

**第一类是使用。**

开发软件的最终目的是投入使用，因此，使用软件并报告反馈，本身就是参与贡献。我见过不少数据库开发人员，并不了解数据分析师和业务开发人员等具体用户到底是怎么使用数据库的，生产环境里最常见的用法，最常被使用的 SQL 特性，沉浸在内核开发当中的工程师未必能够非常准确的把握。通过测试软件在生产环境下的表现，使用真实业务负载验证软件最终交付的价值，对开源软件的打磨价值都是不可忽视的。

TiDB 共同体非常重视用户使用。[“我们已经用起来了”](https://zhuanlan.zhihu.com/p/272761218)，是他们最喜欢听到的话。TiDB 的 [AskTUG](https://asktug.com/t/topic/542887) 论坛上每天都有海量的问题。这些问题大部分都比较初级，但是初级问题反复出现，意味着开源项目的文档建设和知识库建设不够充分，缺少一个快速上手的文档和常见问题的列表（FAQ）。除去这部分问题，进阶的问题能够描述清楚一个具体的使用场景和遇到的障碍。这类问题往往可以使用某种技巧绕过，这些技巧集合起来，就是使用软件的最佳实践。

前面提过，开发软件的最终目的是投入使用，而软件最终投入生产是一个复杂的过程，任何一个环节无法满足需求，没有绕过方案，都有可能导致用户放弃使用。而任何软件刚刚发布的时候，都是存在这样那样的问题的。通过使用软件并报告反馈，其实就是常说的“踩坑”过程，逐步把软件使用的“坑”给填平，开源软件触达更多用户也就成为可能。为什么 Java 生态比 C# 生态好这么多？为什么 Python 生态比 Elixir 生态好这么多？相当一部分原因就是在漫长的用户使用过程当中，许多未来用户可能遇到的问题，都被先行者给解决了。

对于具备技术能力的开发者来说，使用上游软件并发现问题，还有可能是深入参与的契机。例如我在改进 Apache Flink 的高可用模块的时候，深入理解了 Apache ZooKeeper 和 Apache Curator 的设计实现，并以此为契机为两个项目做出贡献，并成为 Apache Curator PMC 的一员。

另一方面，上面提到的旅程当中，除了使用者以外，还有一个角色就是答疑者。只有少部分提出问题的人，能够自己解决问题。大部分提出问题的人，都需要有另一个经验更丰富的共同体成员协助解决问题。

AskTUG 论坛有版主机制，赋予积极答疑并愿意承担一定协调责任的成员版主的头衔和权限。通过开放合作，AskTUG 论坛聚集起近十位版主，为解答 TiDB 系列产品用户遇到的问题发挥了中流砥柱的作用。可以从[《TiDB 社区版主，一群平凡又伟大的 TiDBer》](https://asktug.com/t/topic/183426)一文当中窥见一二。

Apache 基金会治下的项目共同体，往往也强调承担答疑职责的重要性和共同体对这种行为的认可。例如，Apache Flink 项目对 committer 候选人的第一个期待，就是能够积极回答用户问题

> Community contributions include helping to answer user questions on the mailing list, ...

**第二类是发布。**

发布一个软件并非易事，[《Perlbrew 中文简介》](https://perlbrew.pl/Perlbrew-%E4%B8%AD%E6%96%87%E7%B0%A1%E4%BB%8B.html)一文中介绍了 Perl 5.8.8 到 5.10.0 版本之间的发布工作燃尽了两位顶级黑客的精力和热情的故事。

这个故事以发布流程的改进为结局，后来的 Perl 版本发布短到一个月内就可完成。不过，发布这一活动作为开源软件生命周期的重要一环这个事实，却从来没有改变过。PostgreSQL 共同体每次发布都会有一个两到三人组成的临时发布团队，并且整个发布流程都被记录在 Wiki 文档里。我在[夜天之书 #20 The PostgreSQL Community](yatennosyo-0020.md) 里有一整段详细讨论。Engula 项目第一份开发者文档，就是[发布指南](https://github.com/engula/engula/blob/bbbfd9bbaa60bdd7b46adf04c9af658da9e67057/docs/dev/release-guide.md)。[Apache 项目成熟度模型](https://community.apache.org/apache-way/apache-project-maturity-model.html)里，也对发布的质量详细区分了五个等级。

软件的发布是持续交付或叫持续部署的一环，涉及的专业知识不比开发软件核心功能少。一个项目有可靠的持续交付，下游用户才能基于它构建起繁荣的生态。

举个例子，我在分析 TiDB 软件工程上的问题的时候，就提出过发布过程和产物不够清晰，版本支持策略未定义等问题。现在的 TiDB 不像 Apache 项目有明确的文件服务器和稳定获取发布产物的地址，而是依靠工具来完成部署。耦合发布和部署不是一个好选择，尤其是在上一个[部署工具生命不过三年](https://github.com/pingcap/tidb-ansible)，[新工具生命不过两年的](https://github.com/pingcap/tiup)的情况下。[Bytebase 支持 TiDB 的旅程](https://mp.weixin.qq.com/s/DXdDvyo9l3r7Uu3HO5cQ9w)当中，虽然不乏对部署工具的赞许，但也指出了新工具只支持新版本的缺点。由于耦合，部署工具不支持，发布产物也就难以获取。另外，文中也直接明了地提出了版本策略不清晰带给下游的问题。

随着开源吞噬软件，融合不同组件的解决方案在交付时如何进行合规审计和安全审计也是一个日渐复杂的问题，这些问题都归属于发布这一开发活动当中。如果你是一个掌握软件持续交付经验的人才，从这个角度切入参与开源共同体将是非常犀利的，这也是当前不少开源项目求之不得的人才。

**第三类是内容。**

围绕开源软件开展内容创作，是几何级数乃至指数级数壮大开源共同体的秘诀。内容创作可以大体可以分为四个类型，即文档、博客、演讲和演示。

文档是最贴近开源软件的内容创作。实际上，不少开源软件把用户文档作为版本交付的一部分。[TiDB 的用户文档](https://docs.pingcap.com/tidb/stable)经常受到赞扬，[Kubernetes 的共同体文档](https://www.kubernetes.dev/community/)也被其他开源共同体用作治理和运营的参考材料。

类似的例子数不胜数。一位经验丰富的技术写作者在交流过程当中曾经提到，好的内容创作能够简明扼要的抓住潜在参与者的注意力，在这个信息爆炸的社会当中为开源共同体赢得劳动时间的投入。

好的用户文档获取用户的注意力，提高软件普及程度，扩大开源共同体生存的基本面。好的开发者文档获取参与者的注意力，减少参与贡献过程当中的摩擦损耗，提高协作效率。好的愿景和价值观，能够聚拢起志同道合的参与者长期为项目发展持续做出贡献。

高质量的文档，必定基于对核心开源软件的理解，对受众的共情，以及文字写作的功底。Apache Pulsar 的 PMC 成员 [Jennifer Huang](https://lists.apache.org/thread/22zl46xlthzk8lmmcdm2r3vhcn4nn5qf) 正是出于为 Pulsar 共同体创作技术文档等内容而收获认同的。

博客可以认为是文档的延伸。它是不那么正式的，具备个人风格的内容。同样，许多知名的开源项目，在文档之外都会维护一个博客列表。开源共同体当中也会传阅列表之外的优质博客。例如，我一下子就能想起来 Flink 相关的两篇让我获益匪浅的博客。

* [基于 Flink SQL 构建流式应用](https://wuchong.me/blog/2020/02/25/demo-building-real-time-application-with-flink-sql/)
* [Flink 1.11 Unaligned Checkpoint 解析](http://www.whitewood.me/2020/06/08/Flink-1-11-Unaligned-Checkpoint-%E8%A7%A3%E6%9E%90/)

类似的例子也比比皆是，我在撰写 This Week in TiDB 期间也多次引用了共同体成员发布的高质量博客。博客的下一步就是书籍，例如 Eric S. Raymond 为 Linux 共同体做宣传的[《大教堂与集市》](https://book.douban.com/subject/25881855/)。很明显，这些内容的传播效率较之软件代码、改进提案和用户文档本身，具有更好的传播效果。这一点还体现在中文社群当中多有对知名开源项目提案的解读上。

* [JEP 402: 统一基本值与对象](https://zhuanlan.zhihu.com/p/354979657)
* [2022 年异步 Rust 的改进计划](https://mp.weixin.qq.com/s/Vr9IQIGvevimeo_A2_I3KQ)

演讲的传播效果较之博客又要更进一步，因为它不需要受众阅读并理解文字的含义，而是通过视听体验直接获得感觉。Linus 的经典演讲相当之多，他在这些演讲当中表达的观点为 Linux 项目聚拢起志同道合的核心成员发挥了重要作用。

* [Linus Torvalds on his insults: respect should be earned.](https://www.youtube.com/watch?v=JZ017D_JOPY)
* [Linus Torvalds - Nvidia F_ck You!](https://www.youtube.com/watch?v=IVpOyKCNZYw)

Flink Forward 大会，KubeCon 大会，COSCon 中国开源年会，越来越多开源共同体举办的峰会集中输出开源文化和开源软件的价值，以影响整个软件行业对开源软件的认识和使用。作为开源世界的意愿，无论是参与演讲还是运营支持，以至于发起峰会，都是对开源共同体壮大的重要贡献。

* [Flink Forward](https://www.flink-forward.org/)
* [Panel Discussion: How to Attract Developers to Join Your Community](https://www.youtube.com/watch?v=BbDUZFGJoHw)
* [COSCon'21 第六届中国开源年会](https://space.bilibili.com/525037536/channel/collectiondetail?sid=63363)

最后要讲的是演示。演示可以融入到上面提到的三种方式当中。例如，文档可以加入快速开始的演示项目，上面提到的《基于 Flink SQL 构建流式应用》博文本身就是一个示例应用的讲解，演讲当中也经常插入演示环节增强表现效果。

单独谈论演示的原因，自然是因为它非常重要。在信息爆炸、注意力稀缺的今天，短视频以其能够快速抓住眼球，从而大量占用用户时间成为应用新贵。演示起到的就是一个类似的效果。例如，[Perl 的代码诗](https://en.wikipedia.org/wiki/Black_Perl)在相当一段时间内吸引了众多开发者的兴趣和尝试。例如，[TiDB 的热力图活动](https://zhuanlan.zhihu.com/p/379477275)既强调了 TiDB 重视可观测性的调性，又足够有趣以吸引潜在用户试用。例如，[太极图形的太极开物宣传视频](https://www.bilibili.com/video/BV183411E7Ua)就将它在计算机图形学领域的先进性和应用价值生动的传达给每一个观众，相当惊艳。

在软件开发越来越趋于复杂的今天，能够通过演示为开源共同体赢得更多的关注乃至劳动时间的投入，就是为开源共同体做出的重大贡献。

### 再谈代码贡献

如同我在《Why Contributors Stay and Grow》演讲里最后要回过来强调的一样，虽然比起代码贡献，代码之外的参与种类繁多，并且能够达到的传播效果远超代码贡献本身，但是开源共同体的价值，始终是建立在优秀的开源软件之上的，而开源软件，说到底还是代码支撑起核心功能，编译产物是交付物的主要内容。

我们在强调 Community Over Code 的时候，需要避免过犹不及。Community Over Code 不应该忽略核心成员的能力和影响力，开源共同体的价值核心，还是依靠这些核心成员尤其是写出最初的代码，一开始规范软件开发流程的人来定义的。用户使用和反馈也好，内容创作也好，前提是有一个好用的软件。虽然上游软件应该适应下游需求来创造，但是最终形成的开源共同体，还是上游定义的软件及围绕开发软件的共同体的价值观推向下游的。

这一点很好理解。创作 GNU 系列项目的人，通过软件及共同体传播自由软件的理念。Linux 选择了 GPLv2 协议，进而影响了整个 Linux 发行版的生态的调性。试图抛开软件，抛开具体的核心成员，定义一套任何人都可以采用的方案建设成功的开源共同体，是不切实际的。这就像是没有一个确保成功的创业法则一样。

只有深入参与到共同体的发展历程当中，通过长时间的投入赢得声誉，建立影响力，并且对软件的定位和共同体的价值取向有相当的理解，对参与共同体发展的核心成员乃至所有成员都有良好的联系，才能够结合具体的情况从共同体层面为现在该干什么，下一步该怎么走做出正确决策。

## 我应该怎么做到？

为什么要解决这个问题？

内容

论坛

聊天室
