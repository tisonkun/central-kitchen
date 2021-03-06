---
title: '夜天之书 #40 开源共同体参与者的动机'
---

本文整理自我在开源社举办的 COSCon'21 活动上的主题分享[《Why Contributors Stay and Grow》](https://www.bilibili.com/video/BV1Tg411K7KS/)的第一部分。

正文开始之前，简单讲讲题目中的两个名词。

一个是相比起开源社区，我现在倾向于使用**开源共同体**来指代 open-source community 的概念。这个词借鉴自科学共同体，科学共同体是由科学观念相同的科学家所组成的集合体，也即科学活动的主体。我认为开源软件的开发以及围绕开源软件开展的活动更加贴近这类共同体的概念，而不应与街道社区的概念混淆。关于这个词的详细阐述，可以参考[《根本就没有什么所谓的“开源社区”》](https://opensourceway.community/posts/community_leadership_development/what-is-open-source-community/)一文。

另一个是相比起贡献者，我现在倾向于使用**参与者**来指代 contributor 的概念。因为我认为 contributor 参与到开源共同体当中是以他们亲力亲为的行为来支持共同体发展，这是一种赢得声誉的方式，而不是近义于奉献的贡献。关于这个词的翻译，我还不够满意，做出贡献本身也是中立的，只是容易被误会成无私奉献。

开源运动持续吸引新的参与者加入，围绕开源软件建立起来的生态也越来越繁荣复杂。在这样的背景下，形形色色的参与者的动机也各有不同，我将这些动机分成三类。

## 直接利益

一开始，自由软件运动当中的黑客虽然能够销售自己编写的软件，但是由于软件本身以自由软件协议许可，所以这类直接利益实际上非常有限，对于参与者来说也不是主要的动机来源。

随着开源运动的影响力日渐增长，针对性的运营岗位和运营预算的出现，导致参与开源软件的开发或者以其他形式为开源共同体做出贡献能够实际获得直接利益。例如，提交补丁赢得马克杯或者文化衫等小礼物，参加改进开源软件的挑战赛赢取奖金，或者有偿为开源软件撰稿及宣传等等。这类动机下参与到开源共同体的人，都可以归类到直接利益激励之下。

这类参与行为的特点是成果可以明确衡量。例如，提交多少个补丁，反馈了多少个问题，挑战赛下每个题目的积分以及是否被解决，稿件是否交付，宣传的效果包括文章阅读量，视频播放量，植入链接点击转化率等等。

我并不反对这种参与动机，因为无论是出于何种理由，参与到开源共同体的建设当中，支持它的发展，都是实质的贡献。只是对于发放直接利益的运营人员，或者认为如此运营非常有效的决策者，需要提醒一句不要高估了这种参与的价值。

实际上，面对各个开源项目推出的五花八门的活动，有不少人会专门盯着这些消息，计算其中门槛低，收益高的活动去参与。例如，开源项目刻意放出诸如修复 linter 等机械化的待办项，完成一个或几个就可以兑换主题小礼品。例如，为了挑战赛的奖金，选择一个与开源项目勉强挂钩的自己熟悉的主题参赛。事成之后，也就把项目完全抛诸脑后，物色下一个“送财童子”。

求仁得仁。既然提供直接利益的衡量标准就是数字化指标，那么如此运营最终也就会得到相应的指标。但是，发展开源共同体需要有责任心的参与者。这样的活动如果不是根据共同体发展的实际需要顺势而为，而是刻意为之，例如故意留下缺陷找人修复，那么为此而来的参与者就不会尊重这个项目，而有责任心的参与者和维护者，也不会重视这样的活动。到头来只是劳民伤财，甚至培养出核心参与者和活动参与者之间的矛盾，真是得不偿失。

直接利益的激励方式也能够正向的结果。如同上一段提到的，带来问题的活动是刻意为之，如果活动本身是顺应共同体发展而举办的，就不会有这种问题。

第一类，比如 [TiDB 性能挑战赛](https://pingcap.com/zh/blog/how-to-join-in-the-tidb-performance-challenge-program)根据 TiDB 对表达式模块发展的需要，把标准化的任务发布出来并利用宣传渠道和直接利益激励鼓励参与。虽然参与的人大部分也没有持续投入，但是这个活动本身确实解决了 TiDB 的实际问题，且有部分后来非常活跃的参与者是从这个契机加入进来的。

第二类，比如各个开源项目每年参与 [GSoC](https://summerofcode.withgoogle.com/) 等活动的主题。这类主题一般是把项目重要而不紧急的工作借力第三方渠道发布出来，利用第三方对自身品牌的需要和投入，吸引相应的参与者合作开发，最终由第三方支付直接利益报酬。这类活动比起标准化的任务，通常更具有独特性，参与其中的成员也更有可能留存在共同体当中持续贡献。

第三类，比如 Perl 共同体的 [Grants](https://www.perlfoundation.org/grants.html) 流程。这是从近二十年前开始的一个拨款项目。类似于其他非盈利组织，Perl 基金会接受社会各界的捐助。不同于 Apache 软件基金会和 Linux 基金会，Perl 基金会专门有一部分款项是提供给为 Perl 共同体做出贡献的参与者的。任何人都可以提出拨款请求，说明自己想要完成的项目，预计投入的时间精力和估算的应得报酬。只要拨款委员会认同，就可以成立一个新的工作项。申请人需要落实工作，定期汇报并在完成工作后由委员会验收确认发放拨款。

不得不说，Perl 共同体的运营能力首屈一指。我在 Perl IRC 聊天室里曾经多次听到核心成员包括 Larry Wall 谈论如何优化 marketing 的事，这在其他开源共同体当中是少见的。一个典型的例子是 Perl 6 项目在 2008 年收到了一笔二十万美元的捐款，而后来 Perl 6 的核心开发者 @jnthn 也多次为自己的工作申请拨款。从上面提供的 Grants 网页当中探索，你就可以发现 Perl 共同体是如何利用这一机制推动项目发展的。这种自发捐赠为参与者提供直接利益激励，以达到维持软件迭代开发的手段，在如今以 [DAO](https://en.wikipedia.org/wiki/The_DAO_(organization)) 等形式继续探索，有志于这个方向的人，不如看看 Perl 共同体二十年来都是如何运作的。

## 组织驱动

另一类参与开源共同体的动机是组织驱动。组织驱动的意思是参与者受雇于某个组织，这个组织的存续和发展依赖于开源共同体的存续和发展，在这种情况下，组织有动力通过支付报酬和挂钩绩效等方式，推动其雇员参与到开源共同体当中。

根据组织动机的来源，这类参与动机又可以继续细分。

第一类是组织的业务发展依赖于开源软件，为了保证这个依赖的稳定供应，组织投入人员参与维护，并赢得话语权以推动有利于组织发展的工作。

典型的是发起该项目的公司，例如 PingCAP 之于 TiDB 或谷歌之于 Kubernetes 等等。进一步推广，任何基于开源项目提供商业服务或解决方案的公司，例如 Tetrate 之于 Istio 或 DataStax 之于 Apache Pulsar 等等，都有动力发动其雇员全职参与开源软件的开发和维护，甚至直接雇佣开源软件的核心维护者。

除去这类销售基于开源软件的商业产品的公司，另一类不可忽视的是核心业务建立在开源软件之上的公司。前段时间的 Log4Shell 事件和 Faker.js 删库事件，提醒了采用开源软件构建自己核心业务的公司，不应该把开源软件彻底当成免费的午餐，而应该按照合理的软件供应链安全视角看待开源软件的使用。软件采购本身可能是免费的，但是维护和保障却不是。无论是自己投入员工积极维护，还是购买开源软件服务供应商的服务，都是可行的策略。这两种应对策略，也分别直接或间接地参与了开源共同体的发展。

关于开源软件供应链的详细讨论，可以参考[《我所理解的开源软件供应链安全》](https://zhuangbiaowei.github.io/opensource/2021/05/12/about-OSS-Supply-Chain.html)和[《再谈开源软件供应链安全》](https://zhuangbiaowei.github.io/opensource/2022/01/15/Talking-again-about-OSS-Supply-Chain.html)两篇文章。

第二类是组织通过发起或参与开源项目，来赢得自己的品牌。品牌对于人员招聘和漏斗转换都有不可忽视的作用。谁不愿意为了一个伟大的目标而工作呢？谁不想要在一个技术实力强劲的组织当中开发代码锻炼自己呢？谁不倾向于选择一个品牌文化上更值得信任的组织的产品呢？这方面的例子不胜枚举，尤其是个体价值崛起的今天，年轻人在选择就业的时候，相当一部分倾向于选择能够参与令人兴奋的开源项目的工作。

第三类是组织通过发起或参与开源项目，来定义行业的标准。典型的例子是 Kubernetes 的初始成员，合力把 Kubernetes 做成了容器调度的标准，从而使自己的前期投入都获得了巨大的回报，同时打击了下注给其他解决方案的竞争对手。

另一个例子是世界上大规模使用 C++ 来开发项目的公司，往往都在 C++ 委员会当中有一席之地。谷歌、苹果、微软和 IBM 等公司都是如此。如果能够参与到行业标准的定义，对于保证自己的业务能够持续的受到整个开源共同体工作的增益至关重要。又例如 Java 委员会当中对模块化标准的讨论，对预先编译标准的讨论，都牵扯到组织内部数百万行乃至更多的代码在新的软件开发部署形势下是要痛苦地迁移或兼容上游，甚至完全重写，还是能平滑地过度。

开源共同体当中参与者的动机，占比最大的我认为就是组织驱动类型的。

## 自我驱动

虽然组织驱动类型的占比最高，但是支撑开源软件长久的存续和发展，赋予开源共同体灵魂的核心参与者，往往是自我驱动的。

自我驱动分成两个阶段。第一个阶段是对开源软件的认同和责任带来的动力，典型的是开源软件作者希望它能够产生价值，为更多人所用。

不谈 Linux 一类广为人知的项目，我在上周录制某个播客的时候提到的 [Apache InLong (Incubating)](https://inlong.apache.org/) 项目就是如此。项目的主要作者出于对项目的认同和责任，在它从某大公司捐赠给 Apache 软件基金会之后，积极思考如何避免公司内部的使用跟开源软件的开发分化成两套工作流，定义出了统一的开发和发布流程，避免了某些 KPI 开源项目管生不管养的窘境。

软件的作者毕竟是特殊的一个或少数的几个人。随着软件的发展并逐渐为人所知，越来越多的参与者加入进来，喜欢这个项目，或者把职业生涯都绑定在这个项目及其所代表的领域上，这样的人就有成为核心维护者的潜力。

例如，Apache Flink 的 PMC @wuchong 就在长年参与项目的过程中，把自己和项目紧密地绑定在了一起。现在你提及中国乃至世界范围内的 Flink 专家，都很容易能够听到他的名字。这是他从 2016 年参与至今，从 Flink SQL 到 Flink CDC 跨越多个项目的持续参与，积极解答大量用户问题所积累的贡献赢得的声誉。

例如，Netty 的核心维护者 Norman Maurer 在项目发起的三年以后与它结缘，认同它的价值并把自己的职业生涯的相当一部分建立在 Netty 项目之上。从 红帽到苹果，公司变了，核心技术栈却不变。Norman 一直维护 Netty 项目至今，并为 Netty 著书推广。

数不胜数的例子，是开源项目的开放属性带给软件作者和核心参与者跨越职业生涯不同阶段的参与可能性，以及长期参与带来的认同感和责任感。开源软件就是自己的价值所在，这样的自我驱动推动着参与者以年为单位投入到开源共同体当中。

第二个阶段是对开源文化的认同带来的动力。我在 COSCon'21 上讲到自我驱动的时候，幻灯片展示的是三本与开源文化相关的书籍，[《若为自由故》](https://book.douban.com/subject/26314527/)、[《只是为了好玩》](https://book.douban.com/subject/25930025/)以及[《大教堂与集市》](https://book.douban.com/subject/25881855/)。

这里，我把开源运动和自由软件运动的文化并起来讲，虽然它们的关注点略有不同，但是在创造出好的软件并造福大众的这一点上是一致的。RMS 相信自由软件是软件本来就该有的属性；Linus 认为开发开源软件能够选择自己愿意共事的伙伴，并且在 GPLv2 “我赠与你源代码，你回馈我相关的修改”的理念下共同开发；ESR 相信开源软件的开发模式能够创造出更加优秀的软件。他们对开源文化的认同已经固化到自己的认知当中，我想终其一生也不会改变。

对于一个或几个开源项目的认同带来的自我驱动，能够让参与者在相当长的一段时间内持续地投入自己可观的精力。对于开源文化的认同带来的自我驱动，将影响参与者一生的价值判断，以至于在相当广泛的范围内践行自己受开源文化影响的理念。

我认为，分析开源共同体参与者的动机，以发展开源共同体的目的来看，首先要关注组织驱动类型的动机。这种类型的占比最大，且能够提供成建制的投入，帮助开源共同体壮大自身。当然，不是所有的开源软件都要成为类别杀手，不是所有的开源软件都要不断壮大，作为实用工具和胶水层的开源项目也是支撑起整个开源生态不可缺少的部分。

对于所有的开源共同体来说，必须发展的是由自我驱动类型的动机参与的成员。他们未必是一开始就完全是自我驱动的，项目本身的价值，参与过程的反馈，声誉对参与者社交需要、尊重需要和自我实现需要的满足，以及开源文化熏陶下的思想转变，这些契机有可能让一个潜在的核心参与者觉醒，并产生自我驱动的动机。发现这样的人，并适当引导成为共同体的核心成员，能够极大地增强共同体的生命力和号召力。

直接利益的动机可以作为辅助手段使用，但是应该顺应实际需要，且不必抱有太高的期待。
