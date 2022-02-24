---
title: '夜天之书 #42 开源社群简明分类'
---

开源社群是围绕开源软件建立起来的，首先需要有一个可运行的、有价值的软件，然后才有相应的社群。

围绕软件建立起来的开源社群大致可以分为以下几种

* 用户社群，即使用软件或产品的用户构成的社群。例如 [AskTUG](https://asktug.com/) / [Rust](https://users.rust-lang.org/) / [Apache TVM](https://discuss.tvm.apache.org/) 等等。
* 开发者社群。其中可以细分成**生态开发者**和**内核开发者**两种。
  * 生态开发者即围绕软件构建解决方案的人。例如为 Apache Flink 编写各种数据源的连接器，为 Spring Data 接口编写实现，等等。
  * 内核开发者即开发软件本身的人，即常说的核心开发者、维护者。

不同类型的社群的关注点不一样，不是说一个比另一个重要，就像不能说 CockroachDB 比 Kubernetes 重要一样。应对开源社群的几个分类，需要采取不同的策略。

## 用户

对于一个开源软件来说，首要建立的是用户社群。只有持续交付为用户创造价值的软件，软件才有生存的意义。对于托管在 GitHub 上的项目来说，最轻量级的用户社群方案就是 Discussion 的 Q&A 模块，例如 [Apache SkyWalking](https://github.com/apache/skywalking/discussions/categories/q-a) / [NexT](https://github.com/next-theme/hexo-theme-next/discussions/categories/q-a) / [tonic](https://github.com/hyperium/tonic/discussions/categories/q-a) 等等。

可以采取的行动

* GitHub Discussion Q&A 论坛。
* 软件产品定义，用户文档和使用场景推广。
* 地推发展新用户。

## 生态开发者

繁荣的生态是开源软件生命力的重要组成部分。[AirByte](https://github.com/airbytehq/airbyte/blob/b5b09763551e6a6e53775bde74c7b8139e355b33/airbyte-integrations/connectors) 和 Apache Flink 甚至 PostgreSQL 都有丰富的生态。实际上，对于开源社群运营来说，生态是效率倍增最容易发生的方向。一个插件、策略替换点就是一个生态扩展点，推动生态开发者连接他最熟悉的生态是低门槛、持续积累高收益的活动。此外，终端用户最终使用的是解决方案，而不是软件本身。用户的场景可能涉及各种各样的软件，生态的连接能够降低用户组合不同软件构建解决方案的负担。

可以采取的行动

* 技术设计过程中，考虑插件、策略替换点。
* 软件产品或解决方案中与其他生态连接的部分（Connectors 或 Kubernetes 等）定义清楚要做的工作，类似任务发布多方协同完成。

## 内核开发者

内核开发者是项目的核心开发者、维护者。在相当一段时间内，这就是同一个团队内全职开发项目的人。开源社群策略在这个方向上需要做的工作，是从软件工程角度定义项目的调性和开发工作流，并且对所有参与者采取同一套评价标准选择核心开发者和维护者。

可以采取的行动

* 好的软件工程体系，开放的交流沟通，适当的发布节奏。
* 坚实的技术核心，输出技术价值和设计文档。
* 坚实的意见领袖，输出项目目标和开发热情，聚拢起一批相关领域的专家和爱好者。
