---
title: '夜天之书 #19 The ZeroMQ Community'
---

前段时间，开源之书群里 @phodal 提到[《ZeroMQ》](https://book.douban.com/subject/26320636/)一书里用一整个章节介绍了 ZeroMQ 如何认识和运营开源社区。深感有趣，于是以写成这篇读后感交换来中译本借阅。

随着开源协同工作的深入，倍感分析其他社区的运作方式与得失，从多个角度了解开源极有必要。这本书的书评算是一个开端。由于并未深入参与到 ZeroMQ 社区，对其所描述的认识和运营手段也以接受灌输为主，本文主要是精选书中富有价值的观点和分析手段，附带讨论。

前排提示，这本书的中译本机翻痕迹严重，建议阅读免费可得的英文原版[《ØMQ - The Guide》](https://zguide.zeromq.org/docs/chapter6/) 。

以下正文。

整个章节主要分成三个部分，开源社区当中的人文主义，软件工程实践，以及一组成功模式。

**首先看到 ZeroMQ 当中的软件工程实践。**

这一部分也分成三个主题，开发流程，平台工具，以及设计迭代。

本书独特的一点是强调平台工具的选择。

自由软件运动起源于邮件列表上的交流，当下的开源浪潮产生的软件几乎都托管在 GitHub 等代码社交平台上。ZeroMQ 社区的领袖显然注意到了这一点，书中引用的社区公约 [C4](https://rfc.zeromq.org/spec/42/#25-branches-and-releases) (Collective Code Construction Contract) 当中直接写到

* 项目应当使用 Git 来管理代码。
* 项目应当被托管在 GitHub 或等价的平台上。
* 项目应当使用平台的 issue tracker 来记录。
* 开始修改代码前，应当在 issue tracker 上记录问题。
* 维护者应当通过平台界面来接收或拒绝补丁程序。

如今，GitHub 进一步优化自己的协同体验，发布了 GitHub Discussion 这个平台上的小型论坛，以及丰富的 issue tracker 新功能。所有工作尽可能的发生在同一个平台变得越来越重要。这意味着少学习一个用户界面，少一次登录，以及讨论、问题和补丁之间的平滑整合。

ASF 项目以 JIRA 作为 issue tracker 的默认项。虽然 GitHub 即使在近几年努力追赶仍然不如 JIRA 强力，但是多一次登录和学习成本以及不同平台之间网络和策略的割裂，仍然会产生一些不必要的摩擦。随着 GitHub 被微软收购以后迭代速度大幅上涨，其功能满足也将越来越能够满足复杂的软件开发尤其是敏捷开发的需求。

在这个方向上，Apache SkyWalking 是一个好的例子。遵守 ASF 单一 issue tracker 的要求为基础，利用 GitHub issue tracker 和 GitHub Discussion 以 apache/skywalking 主仓库为入口组织起了整个社区的工作和讨论流程。

* [Apache SkyWalking Issues](https://github.com/apache/skywalking/issues)
* [Apache SkyWalking Discussions](https://github.com/apache/skywalking/discussions)

C4 明确了修改代码的核心流程和要求。

* 开始修改代码前，应当在 issue tracker 上记录问题。
* issue 应当明确地描述问题，避免模糊缺乏标准的讨论，避免直接讨论解决方案。
* 应当拒绝 feature request 或 ideas 或 suggestion 等等愿望清单式的内容。
* patch 应当以 pull request 的形式提交。
* patch 不应当直接 push 到代码仓库中。
* patch 合并需要作者以外的 review 意见。
* patch 应当以技术质量或成文风格来评判，而不是个人喜好。

这些规则看起来平平无奇，却对社区的健康发展至关重要。社区是一个开放式组织，其中跨越边界的协同既是自由的，又无往不在枷锁当中。这些规则的约束使得贡献者有一批基础的假设可以依赖和合作，免受注意力分散和过度发散之苦。

例如，issue 应该关注问题而不是解法，修改代码前应该以 issue 记录问题，这两点就被许多开发者所忽视。软件是由代码组成的，但是软件的价值是它解决的问题。依照上面所说的做法，项目的发布历史可以由解决了的 issue 清单来组成。用户可以从中得到他们关注的问题的答案，贡献者可以理解软件在往什么方向发展。代码变更是实现细节，用户往往看不懂，贡献者也很难从变更中反向总结问题。

愿望清单可以记录在单独的地方，但是它跟亟需解决的问题是不同的。书中写到，根据经验，这些只是堆积在 issue tracker 上，直到有人将其删除。进一步说，这其实要求添加新功能也是以解决某个问题为动机出现的。代码变更都是为了解决某个明确的问题，这将让维护者能够简单地根据问题排出优先级处理。

关于 patch 的要求现在已经近乎成为开源软件开发的共识了，唯一需要强调的就是尽量少地创造特例。比如“小”的改动可以直接 push 到代码仓库里，等等。千里之堤毁于蚁穴，严格的要求也许会让你当下变得更慢，但是整个软件稳定迭代而无需返工，才是最明显的效率。

如果还有一点要提，那就是 patch 的 review 不仅不要基于个人喜好，也不要扩大化问题。PR review 一个常见的 bad case 是看到代码变更处或附近的无关问题，希望贡献者顺带解决，或者贡献者提供了问题的一个正确的最小解决方案，而 reviewer 要求作者提供更大范围的彻底的解决方案。

书中没有直言，但是 C4 的两个条款可以应对这个问题。那就是代码变更应当找准问题并提出最小和准确的解决方案，以及维护者应当迅速地合并正确的补丁程序。它是对的，就应当合并。更大范围或无关的问题可以作为新的 issue 单独跟进，不应该成为延迟乃至拒绝 patch 的理由。

关于设计迭代，本书的论点是“为创新而设计”。

在设计的部分，本书讲了三种设计模式。

第一种是面向垃圾桶的设计。这个比喻很形象，意思是设计的目的就是要丢进垃圾桶。

本书以对这种设计模式的批判讽刺了对创意的创意的过分拔高。创意不值钱，没有例外。

良好的设计过程的出发点是收集真实的用户面临的实际问题，随后评估实现解决方案的投入产出比，以及问题的重要性和紧急程度，最后以易用性取胜。

第二种是面向复杂性的设计。这种设计的目的就是为了变得复杂，这是专业团队很容易犯的一个错误。

上面提到的以易用性取胜正是要对抗复杂性的倾向。专业团队找到了有价值的问题，却纠结于让解决方案满足所有需求。这会使得产品为了解决并不紧急的问题即次要问题付出了过高的复杂性。尤其是在如今解决方案的选择空间极大丰富的市场当中，消费者的选择决定了产品的生存。复杂的解决方案终将被一个简单的方案砸的稀烂。

书中对此的分析是，问题的复杂性各不相同，很多时候解决简单的问题比解决真的很难的问题能对更多的人产生更高的价值。如果你允许工程师随机的开展工作，他们大概率会集中于最有趣但却最不值得做的事情上。为了解决这个问题，需要一套“停止机制”，即设置短期的硬性的最后期限，以迫使工程师只针对最关键的问题做出最小最简单的解决方案。

最后一种设计模式是面向简单的设计，跟敏捷开发有异曲同工之妙。

它强调尽快解决最小的问题，发布原型，以使用和反馈来迭代，而不是去尝试基于奇思妙想开展工作。实际上，这就是 Linux 的发展历史。

关于迭代，除了面向简单的设计当中对迭代的强调，本书还介绍了 ZeroMQ 社区抛弃 RoadMap 的历史。

值得强调的是，开源软件的开发仍然需要在一个大致相同的方向上工作，并且聚焦于最有价值的事情上。ZeroMQ 摒弃的 RoadMap 实际上是一种形式主义的，由一小部分专家制定的计划的问题。

形式主义的路线图是僵化的，其实是某种意义上的瀑布模型。书中所说的路线图甚至会拒绝不在其上的功能的开发，这当然是不合理的。因为计划总会出现意外，总是不能如同预期那样发展。随着时间的推移和问题的发现以及解决方案的提出，软件开发的重点是在不断变化的。任何种类的形式主义都将损害贡献者的效率。

此外，由一小部分专家制定的计划使贡献者被排除在外。贡献者不再是为自己的发现和诉求而工作，反而是在解决别人提出的需求，成了一件苦差事。同时，专家也会犯错，个人创造力不如协同流程重要，后者能够激发集体智慧。

不过，开源社区的参与也不完全是自己提出问题并解决，对于贡献者解决他人问题的心理问题，我在[《Drive Cooperation》](yatennosyo-0017.md)里提出“找到不同工作给相应的贡献者的价值”的方法来改变这个过程的价值认知。

最后，一个有机的随着时间推移而动态演进的路线图是有益的。它能够让用户和贡献者知道开源社区真正的发展方向和短期内想要解决的问题。只要对不同时间跨度的承诺有合理的预期，这就是一个有价值的信息同步手段。

**其次，是开源社区当中的人文主义。**

ASF 的宣传片 [Trillions and Trillions Served](https://www.youtube.com/watch?v=JUt2nb0mgwg) 当中反复强调 Community over Code 和开源社区连接人这两个点。

本书的观点大抵相同，它写到，软件是关于人的，软件架构的核心问题由人的心理驱动，而非技术。

本书对软件架构的心理元素分析非常到位，以至于值得一一列举。

**愚蠢。**我们的心智是有限的，总会在某些方面表现出无知。因此，软件架构必须简单易懂。软件架构设计必须遵循简单大于功能的法则。

**自私。**我们的行为只是出于自身利益，因此软件架构必须为有利于整体的自私行为创造空间。自私往往是间接和微妙的。例如，我会花时间帮助别人理解某个概念，因为讲解概念不仅使自己再一次理清问题，也能使别人上手帮助我达成目标或分担工作。

**懒惰。**我们做了很多假设，其中很多是错误的。我们希望能够花最少的努力获得结果或验证假设，因此软件架构必须是简单的，开发体验必须是愉快的。

**嫉妒。**我们嫉妒别人，这意味着我们能够克服愚蠢和懒惰来证明别人错了，或在竞争中击败别人。因此，软件架构必须基于任何人都可以轻松理解的公平规则，创造出公开竞争的空间。

**恐惧。**我们不愿意承担风险，特别是失败会让我们看起来很蠢。对失败的恐惧是人们整体愚蠢地服从并遵循一个团队的主要原因之一。软件架构应该使得验证假设更为简单，让人们有取得成功的机会，而不会因为失败而受到惩罚。

**互惠。**我们将付出额外的努力以惩罚不良行为，并执行公平的规则。软件架构应该在很大程度上有章可循，它告诉人们如何一起工作，而不是做什么工作。

**服从。**由于恐惧和懒惰，我们乐于服从。这意味着如果有一组良好的最佳实践，清楚的解释和记录，并公平地强制执行，我们每次都会自然地选择正确的道路。

**骄傲。**我们强烈地意识到我们的社会地位，并将竭力避免显得愚蠢或不称职。软件架构必须建立起功能模块与其作者的联系，这样我们就会对别人会怎么说我们的工作紧张得夜不能寐。

**贪婪。**我们终究是经济动物，所以软件架构必须给我们投资用于促成工作的激励。这也许是作为专家的声誉，也许是通过贡献技能或组件实际赚到钱。激励具体是什么不要紧，但是一定要有经济诱因。尝试将软件架构视为一个市场，而不是一个工程设计。

**最后，是一组软件工程的成功模式。**

本书使用了“软件工程的一系列的成功模式”来描述这部分内容。其实，开源软件的开发并没有什么奇特的，仍然很大程度上遵守软件工程多年来的积累。唯一的不同在于参与软件开发的成员跨越了组织边界，在开放式组织当中协同开发并发挥出每一个贡献者的效率，是一个很大的挑战。

我不会重复介绍这些成功模式的内涵，仅部分罗列其名目，希望能吸引到各位阅读原文。

* The Lazy Perfectionist 懒惰的完美主义者
* The Benevolent Tyrant 仁慈的暴君
* The Open Door 门户大开
* The Social Engineer 社会工程师
* The Constant Gardener 不朽的园丁
* The Pirate Gang 海盗帮
* The Flash Mob 快闪族
* The Historian 历史学家

回到本书本篇提出的一个大问题，我们可以特意培养开源社区吗？

答案显然是可以的。

ZeroMQ 社区这章中从开源社区当中的人文主义，软件工程实践，以及一组成功模式介绍了 ZeroMQ 给出的答案。限于篇幅和侧重点，关于 Git 和 GPL 的讨论被省略了。

其实在企业当中推广开源协同的实践，其触发点也是特意培养一个优质的开源社区。首先把社区组织起来，再要求全员逐渐加入社区。在这个过程中利用好前文提到的心理学，并坚持和发展软件工程的最佳实践。而不是要求企业的员工一定要怎么样。

社区拉动跨越组织边界的信息透明以及先进的组织运作方式，而不是从推动组织内部变革出发。关注社区的贡献，关注社区当中的人遇到的问题，发展好社区，组织内外的人都是发展对象。这个过程即[《协同》](https://book.douban.com/subject/34834429/)当中所提到的内破部门墙，外拓组织边界。

最后，我想尝试继续这次借阅评书的过程，想要找到以下两本书阅读。预计一本读一个月左右，写一篇书评以后寄回。

* [《公共事务的治理之道》](https://book.douban.com/subject/10545403)
* [《开放式组织》](https://book.douban.com/subject/26894636)

愿意借阅的老板可以直接私信留言，感激不尽！