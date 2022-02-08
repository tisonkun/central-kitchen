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

首先要讲的是评审代码，这是一种经常被忽略的参与动机。因为相当部分开源共同体，总是考核并引导参与者自己写代码和提交补丁，只把写代码当成贡献，而将评审代码视作一种不得已而为之的成本，甚至当做是 committer 和 maintainer 的特权。

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

### 代码之外的参与

### 认识不同类型的参与


## 我应该怎么做到？

为什么要解决这个问题？

文档

论坛

聊天室
