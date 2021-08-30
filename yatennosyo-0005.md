---
title: '夜天之书 #5'
---

今天继续昨天没讲完的两个问题，背景是全球开源技术峰会“开源成功，企业开源办公室（OSPO）先行”圆桌上讨论的话题。[圆桌录像链接](https://play.itdks.com/watch/10468548)，约两小时前后开始，请自行取用。

每天长文还是有点困难，今天在思考一些尚未有结论的内容，也不太适合把杂乱的中间想法乱炖写出来，就先顺着昨天第二个问题，**企业要不要鼓励或者要求员工去开源社区贡献**讲下来。

其实在昨天的讨论中，已经包括了用户阶段和解决方案供应商阶段的企业贡献开源的分析，因此顺理成章的是要鼓励员工去开源社区贡献，或者有实际的人员投入计划，安排或要求员工去开源社区贡献。对于核心产品就是开源产品的企业，这也是不言自明的，只是对于它们来说，会面临如何引导员工以合乎开源社区行为守则的方式贡献开源的问题。

我们不去重复昨天说过的内容，关注到这个问题引发的一个具体问题。

**员工贡献开源以后，被竞争对手挖走怎么办？**

这是在圆桌上直接提出的问题，很现实。

竞争对手掌握企业的组织架构和核心人员名单以后，可以做针对的挖角，因此一直以来人力资源的信息安全在企业当中有着重要地位。

然而，就像[《协同》](https://book.douban.com/subject/34834429/)里介绍的互联网时代的管理挑战一样，新时代下的应届生和从业人员，更加愿意在开放的环境下工作，强个体的价值不愿意从属于企业而存在。同时，为了应对不确定性，组织边界将持续地主动或被动地重新定位，必须发展组织之间的协同才能保证组织的生存。映射到软件开发领域，开源协同就是一个实际的组织间协同的模板。

因此，这不是一个鼓励员工贡献开源与员工信息保密性之间的权衡，而是必须鼓励员工贡献开源，然后思考如何应对竞争对手挖角的问题。

结合圆桌上的讨论，这个问题可以从两个方向入手。

第一个是企业如何看待竞争对手挖角暴露到开源社区的人才的现象。

圆桌嘉宾王泽锋提到，人才跳槽未必不是一件好事，Kubernetes 的三个创始人也没有一直留在 Google 公司。这几个创始人出去以后，给整个 Kubernetes 的生态带来了翻天覆地的变化。微软挖了其中一位，随后 all in Kubernetes 生态。另外两位成立了创业公司，后来被 VMware 收购，现在 VMware all in 云原生。

确实如此。企业既然需要鼓励员工贡献开源，无法避免带来的挖角难题，**作为开源软件的开发商，可以将重心放在建设一个开源协同的项目社区上**。Kubernetes 是一个典型的例子，Flink 和 Kafka 也是典型的例子。

建设一个开放的社区，并且开源软件本身是领域内技术领先的解决方案。你的员工出去以后，很少会想着重新造一套轮子，这对于他们来说也是抛弃自己过往积累的不明智的举动。他们大多是在新公司推行这一套自己熟悉的技术栈。对于社区生态来说，这是一件好事。无论是可能的站台背书，或是产生修订版以连接广阔生态，并最终贡献回上游社区。至于为什么新公司会这么做，上一篇文章里已经有详细的论述。

对于开源软件的下游企业来说，社区的成长对自己带来的价值是有的，不过实在有些遥远。无论是用户企业还是供应商企业，应对这一难题，**下游企业可以把关注的重点放在吸引和留住贡献开源社区的人才上**。

王泽锋提到，真正对生态有伤害的，是有些雇主不愿意在生态上投入，只是看到社区当中的人才技术比较强，挖角以后投入到商业软件的开发。圆桌嘉宾 Keith 随后补充道，人才也会评估前来挖角的公司，评估它是否有开源文化。

开源文化，直接讲的是认知和行为，实际体现出的一家企业在开源软件领域的影响力。这种影响力，聚焦到某一个项目上，分为硬性影响和柔性影响。这两个词汇有点不符合中文表达习惯，其实是从英文里的 Hard Influence 和 Soft Influence 翻译而来，这种对比可以类比“软技能”的意味。

硬性影响，指的是通过流程规范或治理模型对社区发展和技术演进达到实际的控制。这种情况通常发生在某一家企业将核心产品作为开源产品推出的情况，例如实际上 MongoDB 公司完全控制了 MongoDB 社区的发展，PingCAP 能够相当程度地控制 TiKV 社区的发展，Databricks 对 Spark 的演进方向也能很好的把握。虽然在走向广泛协同的过程中，硬性影响会逐渐削弱，但是它确实能够吸引对开源软件充满热情的人才加入进来，并留住他们在这家代表技术前沿的公司。

柔性影响是一种说服他人相信你的理念的能力。这是没有硬性影响的下游企业应该着重考虑建设的能力，也是终将减弱乃至失去硬性影响的开发商应当重视的能力。

一些现实中建立柔性影响的实践是，参与开源技术会议并发表演讲，赞助开源基金会等实体，和开源软件的上下游建立社区之间的联系以及社区成员之间的私人联系，等等。

柔性影响建立在坚持上。如果你的公司持续的出现在开源技术领域当中，年复一年，并展现亲切的态度与专业水平，社区成员就会相信，这家公司是真的打算长期投入到开源世界中来的。这一切不会发生得太快，你需要一点时间。

开源应当作为企业的战略之一，这篇文章有详细的讨论。

https://mp.weixin.qq.com/s/5XmBEnu8_Xl1YsnwuOX64A

柔性影响建立在信任上。信任不是单向的，上面提到社区成员信任这家公司，反过来通过贡献得到赢得权威的成员也应当得到参与社区的公司的信任。如何建立社区信任体系是一个复杂的话题，但是社区成员能够合并代码或者在决策会议上投出有效票，是一种极高的信任水平。你的公司应当与深受信任的社区成员建立联系，帮助他们解决问题，共同在社区当中创造价值。

除了企业应对挖角的方向，另一个讨论方向自然就是人才应对的方向。

恭喜你，你在开源社区当中的贡献得到了认可，这家公司对你伸出了橄榄枝。那么你应该如何评估这家公司是否值得加入呢？

首先我假设你对开源软件是有热情的，也许像我一样有着通过开源协同的开发方式提升整个软件行业的理想，或者是喜欢与其他开发者共同开发的体验，又或者是希望在交流技术的时候不需要为了保守“商业秘密”而遮遮掩掩或者绕着弯说话。那么第一个建议就是，不要去做闭源的商业软件。

Keith 提到，这些公司会把你招进去，开发一个不允许公开讨论的软件，过个一两年就把你踢掉。这类公司只是看中你的技术能力，与你的理想和追求格格不入，背道而驰。即使它不踢了你，你也几乎无法忍受每一个工作流程当中封闭与狭隘的的感受。还有一些公司声称做开源软件，但是其实是假开源，仅开放源代码。你也不要去，它们的工作流程也是封闭的。

其次，在选择不同公司的时候，也要考虑你在开源社区当中积累的技术经验和开发习惯。你在 Flink 做了几年的流计算，突然跑去做 API 网关，这个几乎是转行的沉没成本是很显著的。即使是同样的领域和同样的技术，不同的位置和身处的环境也会有新的适应成本。

再有，稍微带点理想主义的，转述圆桌嘉宾适兕的观点，要在开源社区当中实现自己的理念，和企业打造自己的柔性影响一样，也需要坚持和长期努力。Linus 并没有被巨头挖走，三十年来坚持发展 Linux 开源社区，有了今天这番光景。Chris Lattner 大力发展 LLVM 的时候，也一直待在 Apple 公司。

最后，前面关于企业应当如何应对人才挖角的议论，也可以反过来用于评估这家企业的开源文化。

其实这个方向还应该再详细讨论个人如何认知贡献开源这件事情，但是时间有限，整个人才应对的方向的讨论写得比较仓促，且待日后再做展开。