---
title: '夜天之书 #26 Four-Factor OSC'
---

今天讲一个拿来主义的观点，开源社区的四要素。

[The 4 Pillars of Successful Open-Source Communities](https://maximilianmichels.com/2020/the-4-pillars-of-successful-open-source-communities/)

本文从上面博文本身出发，结合我在 COSCon'21 上的演讲主题内容讨论。

[COSCon21 开源文化 (GL) 论坛介绍](https://mp.weixin.qq.com/s/OuCJt2cBkJ9J86ink7IJew) 关注 Why Contributors Stay and Grow 主题。

再次强调这是个别人的观点，我觉得有一定的价值做转述和分析，不完全是我个人思考或者完全认同的观点。

不过，近期我对开源项目运行过程中处理和商业公司的关系有独立思考得出的阶段性结论，可以关注到相关的开放式讨论，我会尝试总结成一篇文章。

[The relationship between community and company](https://github.com/flossway/flossway/discussions/2)

原博文作者 Maximilian Michels (@mxm) 是 Apache Flink 和 Apache Beam 的 PMC 成员，没想到针对 Open Source 聊了不少内容，博客定位和本公众号甚至有点相似。他也是我在 Flink 项目里交流合作起来比较愉快的一个人。

原博文关注点比较多，我们从标题提到的四个关注点入手。它提到，一个成功的开源社区有四大支柱

* Code
* **People!**
* Processes
* Ownership

## Code

我在 COSCon'21 的演讲里提到 contributor 来到社区以后，会有两个问题。第一个是**我能为社区做什么**，第二个是**我该如何做到**。展开第一个话题时，我分成了三个点来讨论。

* Code
* Beyond Code
* Fundamental Code

也就是显而易见的代码贡献，以及包括测试、发布、文档、博客和活动等非严格代码贡献。但是最后又强调了 Fundamental Code 这一点，即开源软件是开源社区的基础。

这是为什么呢？

虽然在 [The Apache Way](http://www.apache.org/theapacheway/) 一类的经验之谈当中会提 Community Over Code 的观点，但是这绝对不是说 Code 无关紧要。上面提到四大支柱的时候我们加粗强调了 **People!** 也是受此影响，但是还是应该正视代码以及软件本身的基础性地位。

不止一位开源先锋说到，要想打造一个成功的开源项目，项目本身应当是有价值的，能够解决某类用户在某种场景下的需求。例如 ClickHouse 在分析领域针对能够做大宽表的场景做到了性能的极致优化，Flink 成为了 Stateful Streaming 的事实标准。这都证明，只有项目提供了 contributor 直接或间接关注的价值，它才是有吸引力的，才能围绕项目打造一个开源社区。

关于代码的基础性，原博文的一段论述非常详尽，这里直接全文复刻。

> Code also attracts a certain type of community. Innovativeness, ease of use, complexity, and the programming language play an important part in what kind of community evolves around a project. For example, compare a Lisp project with a Javascript project. Compare system software like a database to a web framework or a JS library. The type of code has a huge impact on the type of community that grows around a project.

不同的项目会吸引到不同的人，开源社区隐含的是围绕开源软件建立起来的人的社区。作为社区，人以及人的连接是至关重要的，但是社区仍然必须提供一个富有吸引力的开源软件。

## **People!**

我在 COSCon'21 的演讲以 Why Contributors Stay and Grow 为主题，开篇的时候就提到“社区”不是一个自然人，它的成长依赖于成员即 contributors 的成长。

当然，一个社区的人群组成是多样的，但我们都以 contributor 统称。演讲中主要关注的是围绕开源软件本身开展活动的开发者等人群，实际当中还会区分出项目的维护者，文档博客作者，活动组织者，布道师，意见领袖，纯粹的爱好者，以及用户。用户当然也是 contributor 的一员，无论是使用本身还是进一步站台或提供反馈，都是对一个社区有意义的贡献。

对人群多样性的理解有一个典型的迷思，即认为开源社区的 contributor 都应该付出一切去帮助别人，都能全身心的投入到开源软件和开源社区的工作里。实际上，这不是天经地义的，而是应当赞许和感谢的。

[对话吴晟 丨 真正伤害开源的是开发者本身](https://my.oschina.net/u/4489239/blog/5047833)

> 真正伤害开源的，还是开发者本身。最常见的两个问题。一个是开发者，特别是中国的开发者认为，软件作者去帮助他人是天经地义的，因为整个软件是你写的，所以我来问你问题，你就应该有问必答。如果你不答，就认为你这个人摆架子。而不是考虑因为软件作者用了自己的时间提供服务，所以应该表示感谢。

原博文提到的另一个点是 The Critical Mass 的概念，这有点像 [Drive Cooperation](yatennosyo-0017.md) 提到的先锋队。先锋队是贡献者技术领袖和意见领袖，他们是调动社区力量的中枢。他们在社区当中讨论演进方向，设计开发代码，分享工程实践，树立行为标准。

当代软件开发越来越复杂，先锋队几乎总是由一群人而不是一个人组成的。对于一个起步的开源社区来说，刚开始可能只有少数几个人是社区活动的核心。但是随着社区的健康成长，这个核心也会健壮起来。前文提到，不是所有 contributor 都能全身心的投入，但是先锋队相比起来是愿意投入更多时间和精力的。这是 Earn authority by contribution, not by position 原则的体现。

有些分析开源社区治理模型的观点会讨论“仁慈的独裁者”模式，也即是先锋队只有一个人，或者有一个人与众不同。如前所述的原因，这种模式越发的少乃至已经消亡了。Perl 社区今年整的治理组织 [Steering Council](https://github.com/Perl/perl5/blob/blead/pod/perlgov.pod) 并不包含 Larry Wall 这个原作者，Python 社区也早就不是 Guido van Rossum 说了算。Meritocracy 是开源社区治理模型的必然。

治理模型的话题下还有一个点是简单才是王道。这个话题是上一篇文章 [Evolving TiDB Governance](yatennosyo-0025.md) 的重点之一。Maintainer + Committer 乃至早期只有 Maintainer 都足以支撑起一个社区的运转。

最后是维护社区当中人的连接需要时常有线上线下的活动。纵观成熟壮大的开源社区，无不有多种多样的 Meetup 和会议以及本地社群。开源社区也是社区，人来到社区的一个重要诉求就是寻求人的连接。

我在总结 Apache 基金会 building community 的方式的时候，就有一节专门讲线上线下活动的形式。

Meetup 通常是半天的小规模聚会，通常有 3~5 个主题分享，避免冷场和选择受众。Meetup 的主要目的是会面以及非正式交流，因此线下 Meetup 的效果远好于线上。各种社区基本都会举办自己的 Meetup 活动。

Forum 或者叫 Conf 是大型聚会或者叫论坛会议，通常会持续 1~3 天，多的会把议题分类到不同主题下，复杂的会提供培训等等。典型的 Conf 包括 ApacheCon 和 KubeCon 还有 Flink Forward 等等。

某些社区还会有自己独特的活动。例如 Perl 社区的 [Perl Advent](https://perladvent.org/2020/) 会在每年的降临节期间每天发布一篇博客，Perl 技术相关以外不限主题，任何人都可以参与。例如 Apache Pulsar 社区的 [TGIP](https://github.com/streamnative/tgip) 活动会在每周五做一个定期的主题分享。这些特殊的活动都有助于社区形成自己独特的文化和认同感。

## Processes

关于流程的问题以前的文章陆陆续续讲过很多了，不在本篇里赘述。如果只有一个原则，那就是**简单才能持久**。另外就是要写下你的流程，在实践和讨论中不断演进，不要搞成潜规则村规。

原博文在这点上也是简单分点罗列了关注点，包括四个

* 工作流 workflow
* 沟通 communication
* 决策 decision-making
* 合规 legal

每一点的内容以后还会持续撰文讨论，这里不再展开。

## Ownership

Ownership 这个词本身我会理解成类似目前研究开源社区常说的归属感。本来我是想把四要素都翻译成中文的，但是 ownership 这个词实在不好翻译，就全保持英文了。

关于 ownership 我在 COSCon'21 的主题以 contributors 的动机开头，这个部分的终点就是认同感与归属感，以共同成长结尾，讲的也是 contributors 在社区当中的主体地位。

原博文对于 ownership 倒是从本意所有权出发，从治理模型和许可证入手讨论。越是了解和分析开源社区，越是感慨许可证和合规对社区健康成长的重要性。合规保证了项目成长的安全需求，不会面临形式上的颠覆。关于这一点，我还在阅读[《Open Source for Business》](https://book.douban.com/subject/35309516)的过程里做思考，暂时不做展开。

原博文将许可证分为四种类型。

第一种是没有许可证，随意用。这种情况其实对于作者是有风险的，因为没有免责声明，有些国家或地区的法规会追究作者其他人使用其作品带来的后果。

第二种是宽容的许可证，典型的包括 Apache License 和 BSD License 以及 MIT License 等等。这些许可证仍然允许你做“任何事情”，但是有一个完善的法律描述框架，包含免责声明，软件分发以及品牌和专利归属的详细条款。

第三种是 Copyleft 许可证，最典型的是 GPL 系列。它的主要诉求是如果你分发了被许可软件的修改版本，这个修改版本应该要贡献回上游社区。贡献不代表合入，而是相同条款下源码可得。这也是开源许可证领域理解和实践起来最有挑战性的一类。

第四种是专有许可证，典型的是 Business Source License 等。值得注意的是原博文将 Open Core 划入了专有许可证的范畴。

关于治理模型，原博文讨论了“仁慈的独裁者”模式和基金会模式，上面 **People!** 一节已有讨论，观点相似，不再赘述。

## Conclusion

原博文的主题是成功开源社区的四大支柱，最后以五大原则总结。

* Communicate openly
* Document well
* Innovate frequently
* Recruit always
* Foster relationships, e.g. via Meetups/Conferences

Communicate openly 以前也聊过很多了，包括 [Public Design](yatennosyo-0015.md) 和 [Open Discussion](yatennosyo-0016.md) 等，是一个社区构建起人的连接的基础。不要私下讨论！

Document well 指的是积极沉淀总结，不要有潜规则村规。

Innovate frequently 强调演进，我理解包括了软件和社区，跟 [Evolving Governance](yatennosyo-0018.md) 提到的“因地制宜”，“与时俱进”有相通之处。

Recruit always 说的是要主动地吸引人才加入社区。

Foster relationships 关系培养和维持，本文说了很多了。
