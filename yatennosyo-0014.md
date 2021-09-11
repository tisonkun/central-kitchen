---
title: '夜天之书 #14 Respond second'
---

预计接下来一段时间的主要输出方向是 Open Source Collaboration 开源协同。

今天作为内容转换的过渡时期，讲一讲开源社区当中的一种行为准则。

**Think first, respond second.**

望文生义，开源社区当中交流和行动时，应该三思而后行。

这其实是一个放之四海而皆准的行为准则，急于表达意见或是采取行动，而未加以深入的思考，很容易词不达意，引起误会甚至恶劣的影响。

互联网时代，你的言论或是行为将几乎总有人记录下来。开源社区讲究公开决策，观点可溯源，更是如此。另一方面，缺少面对面的压力，通过文字来表达自己的观点和意见，原本应该便于字斟句酌。

然而，意见与感受主导的大环境下，还是有太多的人不顾其言论广泛的影响和本可推敲之后再发言的机会，急于发言造成意想不到的后果。

最近几天，一场与名字相关的争论引爆了开源圈子，其中不少言论就有这样的影子。

我们不去聊这个案例，转而看向同期发生而关注度较低，整个过程却很典型的案例。

[Consider renaming project. DataFuse is too similar to DataFusion.](https://github.com/datafuselabs/datafuse/issues/654)

开源数据仓库的新秀 Datafuse 在几个月前收到了上面这个以 issue 形式出现的请求。DataFusion 的主要作者 Andy Grove 关注到这个仓库并建议 Datafuse 考虑改名以避免潜在受众的认知冲突。

DataFusion 是著名 Apache 项目 Apache Arrow 的子项目，为 Arrow 的内存格式提供查询执行的扩展。简单来说，DataFusion 基于 Arrow 搭建了一个简单的查询引擎，跨出了 Apache Arrow 的生态在计算方面的一步。

Datafuse 是几位数据库资深开发者，Apache Arrow 和 ClickHouse 的双料拥趸，开发的一个开源数据仓库。由于它还在很早期的阶段，并且有商业背景影响其宣传手段，这里不对其号称的定位做传播或点评。

我们来看这个案例当中几轮有趣的交锋。

**Name is cheap.**

第一轮的亮点是这句话。Andy Grove 提出问题以后，Datafuse 的主要作者之一 BohuTANG 表达了对 arrow-rs 和 DataFusion 的感谢，认可相关代码的启发和借鉴以后，做了这样的回复。

> For the name, we like datafusion a lot and of course datafuse. Name is cheap, what matters is the code and what problem it solves!

这里的 Name is cheap 显然是受到 Linus 的名言 Take is cheap 的影响。这里其实有一个文化隔阂，Linus 之所以被人说脾气不好，他说的话不怎么客气是很重要的原因。这句话说下来在讲汉语的中国人眼里，大概就是玩了个梗，然后强调关注代码而已。无法体会到英文表达当中的倾向和语气，是一个明显的文化隔阂。

这句话听起来，其实是有点“时间会证明一切”的味道的。其实这里的问题不是代码和产品的问题，而是名字纠纷。当你觉得没问题而别人觉得有问题的时候，如果代价小，可以直接接受建议。如果像上面这种已经注册公司，修改代价比较大的情况，如果了解到 Andy Grove 是 DataFusion 的主要作者，最好的做法也是先问一下缘由。

后面的讨论中也提到了，fuse 和 fusion 在英文当中就是融合的动词和名词。对于海外的用户和开发者来说，尤其再加上它们相似的背景和定位，是会带来很大的误会的。

Name is cheap 不是一个好的回答，还有一个有意思的回应。

> If the name is cheap it should cost you nothing to change it, so why not make the change?

这里岔开讲一句，我必须对“相似的背景和定位”做个注释。因为 Datafuse 的阶段相当初步，实际上绝大多数开发者看到这两个项目乃至其他同类项目，都会有所混淆。哪怕是 ClickHouse 的作者 alexey-milovidov 也提出过类似的问题。

[How it is different with Datafuse?](https://github.com/tensorbase/tensorbase/issues/207)

在这个话题下 BohuTANG 的回复有一段是这样的。

> Datafuse is a Modern Real-Time Data Processing & Analytics DBMS with Cloud-Native Architecture.
> 
> Comments are cheap, show me the product and solve actual problem!

还是熟悉的 cheap 味道，而且这个感叹号用得我是真的怕了，给我一种很纠结名词的感觉。但是 Datafuse 的代码确实还很初步啊，写出来再说吧。毕竟现在还只能读内存表或 CSV 的状态，不是你说 Modern Real-Time Data Processing & Analytics DBMS with Cloud-Native Architecture 就是 Modern Real-Time Data Processing & Analytics DBMS with Cloud-Native Architecture 的，未来可能如此，技术交流里真别这样。

**In terms of projects name, the datafuse project has an earlier name than datafusion.**

这个真的有点自欺欺人。大家都知道 DataFusion 是个成名已久的项目，甚至有自己的下游和用户。果不其然就在楼下被立马打脸。

这就是前文所讲的 Think first, respond second 的反例。不要急于为自己辩护，想想别人的诉求是什么，不应该犯这么低级的错误。

**The name datafuse does not harm any community and our team will not do so, and not intended to leverage anyone's halo, if so please let us know.**

对于这一句，马上就有 DataFusion 的贡献者明确的说这个 issue 之所以引人注目，DataFusion 的相关人员之所以有这样的诉求，就是因为这里有问题。

不再重复之前的论断。其实可以看出 Datafuse 团队的成员是真的没感觉到这个名词问题，并且确实有很好的开源社区共建初衷。

> The naming issue is perhaps due to language barriers. In English, datafusion is really similar to datafuse, so it will definitely cause confusions to your potential customers outside of China.

直到 houqp 点出这个语言隔阂，Datafuse 团队才真正理解了问题，并且确定这个是早晚要解决的问题。

sundy-li 随后开始沟通和回应，截至目前，Datafuse 确定要改名但还没想好怎么改。这其实最后是一个好的案例，除去中间部分沟通方式的瑕疵，阶段性结果是 community 就名称问题达成了一致。

值得一提的是，ClickHouse 的作者 alexey-milovidov 曾经开过一个 issue 来沟通过 Benchmark 的问题。

[Check the benchmark of Datafuse](https://github.com/ClickHouse/ClickHouse/issues/27510)

具体内容不做展开，但是最后 Datafuse 下掉了自己基于系统表测出来的 Benchmark 数据。我想说的是 Datafuse 早期强调自己跟 ClickHouse 的关系，放出 Benchmark 来打榜，中期在 README 里删掉 ClickHouse 相关的内容，现在又在这次讨论当中加入了 ClickHouse 和 Arrow 相关的信息。

> Datafuse is inspired by ClickHouse and its computing model is based on apache-arrow.

确实可以看到这个项目的发展在社区关系上遇到了相当的摩擦。希望团队成员能认真对待，了解 Community over code 的社区发展原则，不应该试图以 Xxx is cheap, only code and product stand 的思路来解决所有问题。

最后讲一个额外的问题，好像在原来的 Thread 里已经找不到那个 comment 了。GitHub 的 comment 可以删除，可以抵赖，这不好。

大意是如果改名了以后又跟别人撞车了，怎么办？其实这个事情有成熟的解法。

Apache Incubator 接纳新项目的时候，基金会里的人会仔细关注项目名称在搜索引擎上的表现，评估潜在的名称问题。这些工作跟你注册商标的时候是类似的，不是蒙头命名祈祷不跟其他人冲突的。
