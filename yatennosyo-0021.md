---
title: '夜天之书 #21 Bootstrap Community'
---

今天介绍一个接触开源社区过程中初步起草的社区启动方案。内容比较简略，主要是若干想法的杂糅，还请批评指正。

## Goals

* 基础的沟通渠道，什么渠道和聊些什么。
* 基础的协同手段，开发流程和工具应用。
* 基础的社区材料，贡献指南和行为守则。
* 基础的项目报告，自我回顾和灯塔导向。

## Non Goals

* 过早地关注 LICENSE 和 CLA 等合规问题。
* 制定复杂的社区参与规则乃至治理方案。
* 过度依赖自动化运行，而忽视了社区的本质是人的连接。

> 其中，合规问题的商标注册需要提前解决。LICENSE 和 CLA 的问题如果有专人处理，也应该尽早解决。不过早期的代码价值不高，就算被人直接拿去用也不会有太大的损失。鉴于目前国内开源律师匮乏，创业组合多为技术+运营搭配的情况，可适当延后。后续我也会尽量出一个文章介绍 Running an open-source project under Apache License 的内容。

## Proposals

### 基础的沟通渠道，什么渠道和聊些什么

开发者社区的发展与运营需要有相应的平台，这个平台的重要性和选择的方式可以参考 [Open Discussion](yatennosyo-0016.md) 这篇文章。

对于建设在 GitHub 上的新项目来说，最合适的渠道是 GitHub Discussions + Gitter 的组合。两者之中主要的沟通渠道是主题化的渠道，即 GitHub Discussions 一方。因为即时通信的内容分散割裂的，就算能记录完整的历史也不能够极有针对性的讨论和就某一个话题达成一致。

GitHub Discussions 是目前阶段最适合建设在 GitHub 上的项目的主题化讨论平台。既不需要学习古老的邮件列表，也不需要运维一个论坛，同时跟 issue 上关注与问题解决相区分，专注在开放式讨论上。

那么，GitHub Discussions 上应该聊些什么呢？

**首先，RFC 和 RoadMap 很适合在 GitHub Discussions 上讨论，这些技术内容能够产生最初的价值并吸引贡献者关注这个小型论坛。**

很多项目一开始 issue 来达成这个目标，对于 RoadMap 尚可，但是 RFC 其实不太好。

因为 RoadMap 是唯一的，还可以 Pin 起来，类似 [ClickHouse 的做法](https://github.com/ClickHouse/ClickHouse/issues/17623)，也没遇到什么问题。

然而 RFC 在日后的开发当中作为 issue 的话，会被日常开发工作掩埋，而 Pin 的栏位是不足的。[Pulsar 的解决方法](https://github.com/apache/pulsar/wiki)是用 Wiki 来记录提案，但是也遇到了编号冲突以及 Wiki 不可就地评论的问题。

GitHub Discussions 的设计目的就是为了开放式讨论，RoadMap 和 RFC 都是典型的开放式讨论。可以先在开箱即用的 General 或 Ideas 目录下讨论，视情况开出新的目录。

**其次，可以用于社区事务的讨论和公示，包括新成员加入的公示，阐明社区原则，分享社区当中的 good/bad case 等等。**

**再次，Q&A 可以作为一个早期的用户和开发者问答入口，避免在 issue 里回答问题。**

issue 只关注开发工作或有明确结果的工作项。问题确认为 BUG 或优化项，可以通过引用来做转换。

**最后，可以承载社区成员希望展示自己或者交流的内容，例如协同手段的讨论，Release 的联动，开发周期的参与，等等。**

### 基础的协同手段，开发流程和工具应用

不少所谓的开源项目，基本只是把 GitHub 当成一个纯粹的代码存放仓库，这其实给贡献者参与带来了一些麻烦。

开发流程并不是形式主义的条条框框，而是一组软件工程的最佳实践。无论如何，开源软件也是软件，也在很大程度上遵守软件工程的假设和推论。某种程度上说，开源协同就是以跨越组织边界的贡献者为开发者的软件工程。

对于刚起步的开源社区，只讨论几个基础的协同实践，以避免掉进形式主义的陷阱。

**第一，代码修改都应该通过 pull request 来实现。**

虽然 commit 也可以评论，但是最广为人知的代码改动集散地仍然是 PR。在项目早期阶段可以较快的 review 和 merge 代码，但是保留一个开口以供其他人做事后 review 和评论是有益的。坚持这种做法，将可以避免未来的“社区化转型”，因为一开始所有开发者就是完全以贡献者的身份和方式参与开发的。

**第二，所有的 pull request 都应该关联 issue 即 issue : PR 是 1:1 或 1:n 的关系。**

这也是 TiKV 社区正在努力的方向。

[votes: PR Issue Association](https://github.com/tikv/community/pull/150)

或许这乍一看会自己放慢自己的脚步，但是欲速则不达，你终将因此受益。

核心的原因是，不同的人有不同的关注点。issue 关注问题，而 PR 关注解法和代码变更。你的用户通常不会关注你是怎么解决问题的，而希望找到问题他遇到的同类问题并知道它是否已经被修复或实现。开发者常犯的一个错误就是关注代码而不是解决的问题，这会使你的软件关注点偏离，撰写 release note 的时候也不好受。

另一方面，书写 issue 的过程也是重新整理思路的一个机会。如果即将写下或者提交修改的代码并没有明确的解决一个问题，那么它可能是有风险或无意义的。

可能有人会说，fix typo 等小改动不需要费力写 issue 记录。对于这点，上面的建议是一个大原则，可以适当的放宽。但是需要注意的是，每个人都很容易认为自己遇到的情况特殊。因此，例外越少越好。

**第三，避免采用 Merge Commit 合并代码。**

合并 PR 的时候根据 PR commit 的内容及组织情况选择采用 squash and merge 或 rebase and merge 能够保持线性的 commit 历史，这对于阅读或二分 master commit 历史的人来说是件大好事。同时这也隐式的要求所有变更都以 pull request 进行。

**第四，合并 pull request 需要另一个人的 Review 同意。**

这一开始可能有点难，但它的价值不言而喻。记住不要因此而做只走形式的 review 工作，那还不如不做，至少问题暴露得更明显。

这些协同手段乍一看会让开发速度变慢，但是坚持下去，社区会得到整体的效率提升。

关于开源协同的手段，有两个重要的考虑方式。

其一，如果做这件事的人不是自己或相同背景的开发者，你会如何反应？总是将自己作为开源社区的参与者，并考虑当社区多样性提升以后其他背景的参与者做出相同行为时自己的感受，将有利于避免将社区越做越封闭。

其二，开源协同意味着你的工作不一定由你自己全程完成。当你有一个想要实现的功能，或者大的工作拆解成小的任务的时候，尽早的创建出 issue 来，并随后时不时的补充 label 或更多的描述信息，以帮助潜在的贡献者发现并接手这项工作。这个贡献者也可能就是一段时间以后的你自己，你会感谢之前做过的标记和描述记录。

## 基础的社区材料，贡献指南和行为守则

社区材料包括最佳实践和设计文档等等形成一个社区技术实力的各种内容，它的积累是一个长期的过程。PG 社区的 Wiki 页面之丰富是 PG 社区能够回答绝大多数贡献者问题并保持高质量的开发的前提下，能够持续吸收乃至潜移默化的培养新的贡献者的基石。

对于新生社区来说，一个基础且初步的搭建社区参与体验的工作，就是准备每一个贡献者都必须知道且首先应该知道的材料，并将其置于显眼的位置。

GitHub 有着成熟的约定，那就是贡献者首先会阅读 README 和 CONTRIBUTING 两个文件。进一步的，开放式组织的开源社区的约束力是建立在一系列众所周知的行为准则上的。

要想建立起一个健康的开发者社区，除了提供 CONTRIBUTING 材料告诉贡献者如何上手以外，需要尤其强调的一点就是真正认同和实践所选择的行为准则。

社区材料的进一步丰富需要从沟通渠道处沉淀和总结，可以落实到 GitHub 代码仓库的一个目录下，或者 Wiki 上，甚至 GitHub Discussions 的贴子。具体的选择可再商榷，相差不大。

## 基础的项目报告，自我回顾和灯塔导向

对于项目的领导者来说，定期或不定期的回顾自己的项目，选择一组有价值的指标对社区和更大范围的潜在成员做汇报，是一种有效的自省和建立灯塔的手段。

报告的内容可以发布在 GitHub Discussions 上，并且在社交媒体上做传播。对于新项目来说，每一个月或三个月发布一次足矣，有专人负责市场工作的除外。

报告的内容可以参考一下从 ASF Incubator 借鉴来的模板。

{This project} is a ...

{This project} has been open-source developing since ...

* Three most important unfinished issues to address before next demo/release:
* Are there any issues that users or contributors need to be aware of?
* How has the community developed since the last report?
* How has the project developed since the last report?
* How would you assess the project maturity?
* When were the last maintainers elected?

## 延伸阅读

* [Briefing: The Apache Way](https://www.apache.org/theapacheway/index.html)
* [GitHub Community Guidelines](https://docs.github.com/en/github/site-policy/github-community-guidelines)
* [Guide to Successful Community Building](https://incubator.apache.org/guides/community.html)
* [Apache Project Maturity Model](http://community.apache.org/apache-way/apache-project-maturity-model.html)
* [Quickstart for GitHub Discussions](https://docs.github.com/en/discussions/quickstart)
