---
title: '夜天之书 #37 选择开源许可证'
---

开源正在掀起一轮新的浪潮。

如今的基础软件创业公司，或多或少面临同类开源软件的隐性竞争，以至于当公司想要制造一个新的软件或解决方案的时候，总躲不开“代码是否开源”这个问题。可以说，现在的基础软件如果不开放源代码，那么它的竞争力就会大打折扣。

在这样的背景下，几乎每一个项目创始人都不得不思考一个问题，既然代码必须要开放，那么选择哪种开源许可证能够满足我的需要呢？

文章合为时而著。本文就立足于这样的背景，讲一讲开源许可证的选择。首先声明本文内容没有作为法律依据的效力，仅为个人观点。其中提到的许可证也并非全是开源许可证，包括部分仅与开放源代码有相关性的许可证。

## 选择开源许可证的意义

运行一个开源项目，建设一个开源共同体，包括很多方面的工作。但是如果你问我从哪里开始，除了产生核心价值的软件以外，我会说最重要的是确定项目采用的开源许可证。

不同的开源许可证给开源共同体带来不同的保证。选择一份开源许可证，集中表达了项目创始人对开源的认识，以及其所认同的开源理念。开源共同体的调性深刻地影响到此后每一个阶段的发展，也包括如何基于开源软件创造商业价值。

关于这一点，我经常引用 [The ZeroMQ Community](https://zguide.zeromq.org/docs/chapter6/#Eat-Me) 当中的一节，讲了一个开源许可证的选择导致的不同后果的故事。原文较长，这里不做引用，可以从链接点过去阅读。

## Copyleft

讨论开源许可证的顺序，我认为首先要讲的是 Copyleft 的许可证。几乎所有开源许可证的差异，都可以解释为对 Copyleft 许可证与软件自由相关的条款的修订。

主要的 Copyleft 许可证如下

* [Mozilla Public License, version 2 (MPLv2)](https://www.mozilla.org/en-US/MPL/2.0/)
* [GNU Lesser General Public License (LGPL)](https://www.gnu.org/licenses/lgpl-3.0.html)
* [GNU General Public License, version 2 (GPLv2)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)
* [GNU General Public License, version 3 (GPLv3)](https://www.gnu.org/licenses/gpl-3.0.html)
* [GNU Affero General Public License (AGPL)](https://www.gnu.org/licenses/agpl-3.0.html)
* [Server Side Public License (SSPL)](https://www.mongodb.com/licensing/server-side-public-license)

顺序按照从宽松到严格排列。其中 SSPL 不是严格意义上的开源许可证，但是我认为它的设计出发点与 GPL 系列相同，后面会单独讨论。

Copyleft 许可证的核心思想是“[我赠与你源代码，你回馈我相关的修改](https://www.youtube.com/watch?v=PaKIZ7gJlRU)”。从具体条款上看，这是通过要求修改之后的版本采用实质相同的许可证，其中包括分发需要提供源代码的条款来实现的。简单来说，你修改了 Linux 并且将修改版本分发给其他人，那么这个修改版本也应该以 GPLv2 许可证发布，也就是别人可以获取修改后的源代码。通过这种传递性，保证了 Linux 及其所有的后代版本都是开放源代码的。

Linus 曾经多次盛赞 GPLv2 对 Linux 发展的价值，因为它从条款上保证了整个 Linux 生态都在开源共同体之内。ZeroMQ 的创始人也多次提到选择 GPLv3 使得开源共同体更加团结，每个参与者都在相同的上下文当中工作。

对于上游 Copyleft 许可证许可的项目做出修改版本，将修改版本以相同条款发布，是符合一般认知的。这主要是因为修改版本通常只会产生一个小的差异，开发者不会认为这个小的差异足以形成一个实质不同的版本。

对于 Copyleft 许可证的主要争议，以及上面这么多种许可证的主要差别，集中在什么是修改版本上面，修改版本也被称为衍生作品。

MPLv2 许可证下的软件，其所有的源文件的许可是不可变的，而新的文件可以采用任意的许可证许可，对链接也没有要求。换句话说，MPLv2 认为需要遵循相同条款的派生作品的范围到源文件级别为止。

LGPL 许可证下的软件，派生作品的范围涵盖了所有参与编译的源文件，这里的编译不包括链接等库使用形式。也就是说，除非你只是链接到一个 LGPL 许可证下的软件，否则你是直接改这个软件的源代码也好，把修改放在新的源文件也好，都需要遵循 LGPL 条款分发，其中最关键的就是分发时必须无偿提供获取源代码的方式。这种方式一般就是开放源代码允许自由下载，以前经常发布到 SourceForge 网站上，现在大部分是以 public 代码仓库的形式托管到 GitHub 平台。

GPL 许可证下的软件，派生作品的范围涵盖了共同参与编译和链接的源文件。也就是说，你把某个许可证下的软件和 GPL 许可证下的软件链接起来形成一个可执行文件，它就是 GPL 许可证下的衍生作品，因此它的分发需要遵循 GPL 条款，即无偿提供获取构成这个作品的源代码的方式。

AGPL 许可证下的软件，对派生作品的认定和 GPL 相同，不同点在于对分发的讨论。GPL 认为分发的是可执行文件，也就是当你收到 GPL 衍生作品的可执行文件，你有权获取它的源代码。AGPL 认为除此以外，如果你能通过网络访问该可执行文件，那么你也有权获取它的源代码。

举个例子，如果你要部署一个网站应用，其中包括运行中的 Linux 操作系统。如果你对这个 Linux 做了修改，其实在 GPLv2 下，你也只需要保证拿到这个修改版的人能获取源代码就行，常见的情况是只在公司里发布，公司内部可见。这个时候客户访问你这个网站应用，由于他没有拿到你的修改版 Linux 而只是通过网络访问，他并不能援引 GPL 条款要求你无偿提供源代码。但是如果 Linux 是以 AGPL 许可证许可的，那么他就可以做此要求。

SSPL 许可证对派生作品的认定最为激进。它认为如果你提供的服务栈当中包括 SSPL 许可证下的软件，那么整个服务栈都是 SSPL 许可证下的派生作品，进而构成整个服务栈功能的所有相关源代码都需要按照 SSPL 的开放源代码条款无偿提供。这种派生作品的认定没有得到普遍认可，也被开放源代码促进会（OSI）拒绝认证为开源许可证。主要原因是[开源定义（OSD）](https://opensource.org/osd)当中强调开源软件不应该限制一同分发的其他软件。

不过，我仍然认为 SSPL 的设计出发点与 GPL 系列相同。这是因为它也通过创造出高价值的软件占领市场，通过要求派生作品同样遵循相同条款并开放源代码来达到全世界的软件都是自由软件的目的。不过 SSPL 对派生作品的认定过于激进，我个人也不认同，实践当中应该也非常难以认定什么是“提供服务”。比如我不直接封装相同接口的 MongoDB 服务，而是基于 MongoDB 来搭建某种搜索应用，这个应用是不是服务？很难讲。虽然 SSPL 尝试澄清不做修改搭建网站应用不算提供服务，但是缺乏案例和实证，大部分公司团体恐怕都不敢采用 SSPL 许可证下的软件。另一方面，MongoDB, Inc. 自己并没有把整个服务栈的源代码提供出来。它作为软件的作者，当然有权在商业使用上采用不同的许可证来许可自己的软件，但是这种实质上的破坏对等性实在是令人失望。

我个人非常喜欢 GPLv3 许可证。虽然 Linus 认为 GPLv3 之于 GPLv2 新增的反对数字加密的条款是干涉他人自由，不过我接触到的大部分应用都碰不上这件事，所以这两个版本的差别也不是特别明显。GPLv3 大体上还是遵循了“我赠与你源代码，你回馈我相关的修改”的理念，所谓的“传染性”也是无稽之谈。这么多年了，也没见 Linux 把全天下的软件都“传染”成 GPL 软件，更不用说 Android 已经示范了如何通过工程手段分离与操作系统相关的派生逻辑和应用逻辑，所谓的“强传染性”不过是商业公司为了遏制自由软件的传播生造出来的一个概念。技术上，你的商业秘密可以通过工程手段保护起来，商业价值也可以基于 GPL 软件建立，RedHat 和 iMatix 都是实例。

当然，随着软件形态的发展，尤其是“软件即服务”模式的出现，通过网络提供服务确实是 GPL 当初未曾想到的情形。相比起 SSPL 的激进策略和 MongoDB, Inc. 的不讲武德，我认为 AGPL 在这方面做出了实质性的进展，使得云厂商修改 AGPL 软件后即使只是提供云服务，也需要开放该软件的源代码，从而保证了开源共同体能够拿回每个参与者的修改。注意到 AGPL 并没有对构成服务栈的其他软件提出要求，因此这种源代码和修改的交换是公平的。

AGPL 主要的问题是缺少案例，也就是 Heather Meeker 在 [Truth Social, AGPL, and OSS License Compliance](https://www.brighttalk.com/webcast/17752/521473) 提到的，通过网络分发的形式很难被察觉和取证。

GPL 家族及其所代表的 Copyleft 许可证，我认为是自由软件运动和开源运动在法律上最具价值的前沿探索。实话说，为什么软件链接在一起就构成衍生作品，本身也是无法证明的，更像是从业人员认同的公理。衍生作品的认定，分发形式的讨论，是从自由软件运动开始至今，随着时代的发展和软件行业的进步一直被反复讨论的话题。如果你对开源许可证、自由软件理念和开源理念感兴趣，从 Copyleft 许可证入手肯定是没错的。

Reference:

* [Open Source for Business](https://book.douban.com/subject/35309516/)
* [人话解读 GPLv3](https://mp.weixin.qq.com/s/muPDVThX5S4vsXuM5PEoIw)

## Source Available

正如自由软件基金会在 [Why “Free Software” is better than “Open Source”](https://www.gnu.org/philosophy/free-software-for-freedom.en.html) 和 [Why Open Source Misses the Point of Free Software](https://www.gnu.org/philosophy/open-source-misses-the-point.html) 两篇博文里面提到的，虽然 Free Software 有自由软件和免费软件的歧义，但是 Open Source 的定义也不是无争议的。开源定义（OSD）所指称的开源，跟普罗大众所认知的开源，仍然有一定的差距。

这里面最典型的问题当属“开源是否就是开放源代码”。实际上，开源定义对自由和禁止约束有明确的阐述，但是“开源”一词很容易被理解为开放源代码，也就是我能看到源代码了，就是开源。

这当然是不对的。有这么一类许可证，它们允许你获取和阅读源代码，但却限制你的使用。

* [Business Source License (BSL)](https://mariadb.com/bsl11/)
* [Elastic License 2.0 (ELv2)](https://www.elastic.co/licensing/elastic-license)

上面是两个最典型的许可证，其他五花八门的项目公司推出的所谓“社区许可证（Community License）”的思路也是类似的。

BSL 许可证下的软件，除了对生产环境的使用可能有限制要求，几乎没有其他的条件。但是这个生产环境部署的限制，就是违反自由软件精神和开源精神的。比方说，流数据库 Materialize 不允许其他人部署集群版本。

BSL 许可证是由 MariaDB Corporation Ab 推出的，也就是 MySQL AB 在被 Oracle 收购以后，部分员工出走成立的公司。虽然许可证允许对生产环境部署提出限制的同时，也要求明确许可证的“过期时间”，这个时间不可以超过四年。也就是说，在一段时间后，以 BSL 许可证分发的软件将自动换成另一个许可证许可。实践当中，基本都是四年以后就可以按照 Apache License 2.0 来使用该软件。不过这种“过期时间”仅针对单份拷贝有用，如果发行了新版本，新版本可以基于它发布的日期更新最长四年的“过期时间”。

这个许可证的设计思路类似于专利保护，也就是说我作为软件所有者，将代码公开出来，但是我在前四年拥有提供服务的特权，以此盈利来保证我能够持续的推动这项技术的发展。由于有“过期时间”的约束，我有动力持续做功能迭代。

只是，四年的时间相对软件技术的变革速度来说还是太长了。这基本就意味着在该版本尚有价值的时间里，如果你不是软件所有者，就无法在生产环境产生价值。所以这种条款只是保护了软件所有者，却几乎断绝了形成开源共同体以开源协同的模式开发的可能性。因为其他的参与者在这个模型下不仅提供自己的义务劳动，并且不能使用自己劳动的结果，其结果会被软件所有者，通常是商业公司所窃取。

ELv2 许可证下的软件，类似的，你不能提供该软件的托管服务，也不能破解可由许可密钥解锁的功能。其他的 Community License 大同小异，主要也旨在限制用于提供软件及服务的情形。

我个人的观点是，这类许可证全都是 Source Available 许可证，而非开源许可证。其中 BSL 还算坦荡，也没指望能形成开源共同体，只是保护公司利益，开发上仍然走一家公司雇佣一个团队开发一款产品的思路。虽然我认为这种软件开发模式效率不行，总会被开源协同开发的开源软件所击败，但其本身目的明确，无可厚非。专利保护的思路是说得过去的，只是四年的时间断绝了几乎所有合作的可能。

ELv2 一类许可证，就敬谢不敏了。尤其是现在不少所谓的“开源技术公司”喜欢用 ELv2 许可证来分发自己的软件。这个许可证的名字里都带着 Elastic 的字样，其实你某种程度上是把自己的品牌和 Elastic 的品牌绑定在了一起，既为它背书，又存在着它整蛊给你带来的品牌风险。在限制提供软件及服务的目的上，BSL 和 ELv2 能做到的事情几乎没什么差别，为啥不用一个名称上品牌中立，而且就明说我说 Business Source 的许可证呢？

至于 Elastic 自己用 Elastic 许可证，CockroachDB 也自己搞了个社区许可证，人家乐意请律师团队，用自己写的许可证是无可厚非。这些许可证设计的时候，就是为本公司量身定制的，可不会去想其他公司的诉求。

## Permissive

还有一类开源许可证，如今使用得越来越广泛，这就是所谓的宽容（permissive）许可证。

* [MIT License](https://en.wikipedia.org/wiki/MIT_License)
* [BSD License](https://en.wikipedia.org/wiki/BSD_licenses)
* [Apache License, version 2.0 (APL 2.0)](https://www.apache.org/licenses/LICENSE-2.0)

这些许可证对于专利和声明等等问题有细致的差别，但是在我看来其核心思想都是“拿走我的代码，做任何你想做的事”。当然，有些此类许可证会要求你在使用其许可的软件的时候保留原作者的声明，但对于技术使用来说，这些都不是限制技术使用的约束。

这其中最常用的许可证就是 MIT 许可证和 APL 2.0 许可证了。前者基本就是做了一个免责声明，除此以外可以任意使用。后者则对专利和原作者声明做了一些要求，在不限制技术使用的前提下维护原作者和原作品的名誉，并尽量避免知识产权纠纷。

对于这类许可证，比较需要关注的是和其他许可证尤其是 Copyleft 许可证之间的兼容性问题。对此，有一份信通院发布的[《开源许可证兼容性指南》](https://gitee.com/trustworthy-open-source-community/License-Compatibility)介绍得相当仔细。

值得一提的是 APL 2.0 和 GPLv3 的兼容性问题，这也是经常被拿出来讨论的事项。如果你的软件是 GPLv3 许可的，现在想结合一个 APL 2.0 许可的软件产生衍生作品，这个方向是兼容的，衍生作品可以以 GPLv3 发布。反过来，如果你的软件是 APL 2.0 许可的，现在想结合一个 GPLv3 许可的软件产生衍生作品，这个方向会导致你的软件需要以 GPLv3 发布。简单地说，GPLv3 许可证单向兼容 APL 2.0 许可证。对此，Apache 软件基金会（ASF）有一个页面专门介绍里面的细节。

* [Apache License v2.0 and GPL Compatibility](https://www.apache.org/licenses/GPL-compatibility.html)

由于 APL 2.0 的流行，加上 ASF 要求治下所有项目必须以 APL 许可，这也成了某种意义上限制采用 GPL 的客观条件。以前，当你采用 GPL 许可证的时候，你需要对抗的主要是来自商业联盟的攻击。现在，你还需要忍受开源世界其他软件的迟疑和切割。

## 开源许可证的选择

对于开源许可证的选择，我的建议是

* 如果所属组织或所在共同体有相应要求和惯例，遵循要求或优先考虑惯例。例如 ASF 项目必须采用 APL 2.0 许可证，npm 项目大多采用 ISC 许可证，Rust 项目大多采用 MIT 和 APL 2.0 双许可证，等等。
* 除此之外，优先考虑 APL 2.0 许可证。这是当前环境下最适合建立开源共同体的许可证，并且允许你和整个开源世界友好互动。
* 如果你希望从许可证上保证“我赠与你源代码，你回馈我相关的修改”，那么考虑采用 AGPL 许可证。我由衷感谢每个认真选择 AGPL 许可证的项目，你们都为自由软件运动的发展和探索发挥了不可忽视的作用。对抗商业联盟自不用说，如何与采用其他开源许可证的开源世界联合，将是一个值得探索的议题。

如果你只是希望保证自己的商业利益，开放源代码完全是不得已而为之或者仅供用户参考，不需要发展开源共同体，那么不用考虑开源许可证，可以考虑 BSL 许可证。尤其是，抱着这样心态却又不知道选什么许可证的项目主管，真的别选 AGPL 或者 ELv2 了。前者的设计目的是保证修改回馈上游，不是限制商业竞争，它达不到你的诉求，你会很折磨；后者莫名跟一个不相干的商业公司品牌绑定，没有必要。
