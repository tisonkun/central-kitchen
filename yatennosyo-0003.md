---
title: '夜天之书 #3'
---

今天的话题从前不久的一篇博文[软件工程专业困局](https://zhuanlan.zhihu.com/p/378441006)展开。

这篇文章是我受到[《软件困局》](https://book.douban.com/subject/34907888/)一书的启发，讨论高校在软件工程专业人才培养的问题的。但是成文未免仓促，即使引用了一些例子，整个讲述的过程还是比较抽象。今天我想从学校与产业对软件开发的认知的鸿沟出发，讨论三个容易被学生或是职场新人忽略的组成高质量软件的重要部分。

**第一个是测试。**

经过几十年的发展，整个软件行业大都认可了测试的价值。没有各种测试保驾护航，任何一行代码改动都足以让最老练的开发者胆战心惊。

测试这个话题太大，单元测试、功能测试、系统测试、验收测试和性能测试等等，每一个话题的内容都能够支撑起一本书的容量。我不打算讲太过测试专业的集成测试，只是从最近的例子里见微知著，讲讲跟功能代码结合最紧密的测试的故事。

测试随源代码一起分发，可以追溯到 Perl 语言崛起的年代。虽然 Perl 语言在业内有只写不读的恶名，但是它在软件开发历史上却有不少开创之举。

例如官方维护的 CPAN 中央资源库，这可视作 Maven Central Repository 和 crates.io 等中央资源库的根源，还有模仿 CPAN 的 CRAN 和 CTAN 等等。

例如随 Perl 解释器一并发布的全套测试集，这种风格也影响了 CPAN 上面绝大多数的三方库。这些三方库往往也会在分发的时候带上测试集，当你使用 CPAN 安装三方库的时候，默认就会运行这些测试集来校验三方库是否能在你的本地环境正常运行。

例如，使用 CPAN 安装 ACME 库会看到下面的输出，就是在运行 ACME 库的测试集。

```
t/acme.t ................ ok   
t/release-pod-syntax.t .. skipped: these tests are for release candidate testing
All tests successful.
Files=2, Tests=3,  0 wallclock secs ( 0.02 usr  0.00 sys +  0.10 cusr  0.03 csys =  0.15 CPU)
Result: PASS
```

这种测试和代码亲和的理念影响了许多后来者。例如，Java 开发最常见的 Maven + JUnit 方案组织测试的方式就是 main 目录和 test 目录，共享 package 路径，测试文件和功能代码文件，在同一个代码仓库里。例如，Golang 提供了开箱即用的测试套件和同一路径下测试文件和功能代码文件共存的支持。例如，Rust 提供了开箱即用的测试套件以及更极端的同一文件下测试代码和功能代码共存的支持。当然，极端的共存也会给编译器带来额外的负担，不过这个细节我不想展开。

接下来讲讲测试代码本身的组织。起因是我在 TiDB 社区发起了一个[迁移测试框架的提案](https://github.com/pingcap/tidb/issues/26022)，目的是从缺乏维护的 pingcap/check 套件迁移到被广泛使用的 testify 套件，减轻 TiDB 社区维护一个测试框架的负担，同时享受到 Golang 社区的力量完成的 IDE 对 testify 的集成等等。

对于简单的断言来说，迁移无非就是从一种语法改到另一种语法。但是当单元测试涉及到 setup 和 teardown 逻辑的时候，参与测试迁移的开发者当中就有人有些抓瞎了。这也很正常，因为测试对于大多数开发者来说就像是魔法，调用断言 API 和提供 hook 点的逻辑，就能神奇的跑起来。为了处理某些复杂测试迁移过于机械化带来的代码坏味道，最近费了不少口水。还不如把测试的整体流程都讲一遍，有些问题也就不言自明了。

测试并不是魔法，它也是一个普通的可执行程序。大多数测试框架的组成成分不过三种，Runner 驱动测试执行，测试函数即测试用例本身，以及 Runner 在驱动测试执行的过程中提供的 hook 点，例如 setup 和 teardown 逻辑，JUnit 中的 `@Rule` 资源，等等。

测试迁移的工作在 TiDB 上做，主要是 Golang 的测试。Golang 自带的 testing 套件比较轻量，延续了 package 的组织粒度，除了有个 [TestMain](https://pkg.go.dev/testing#hdr-Main) 提供整个 package 的测试运行前后的 hook 点以外，其他所有的测试逻辑都要手动装配。

Runner 驱动测试执行的核心在于 `func (m *M) Run() (code int)` 和 `func tRunner(t *T, fn func(t *T))` 两个函数。

前者通过反射和字符串匹配找到所有形如 `TestXxx` 的测试函数，并交由后者执行。

后者是测试运行的核心驱动逻辑，通过和 `func (t *T) Run(name string, f func(t *T)) bool` 函数的配合，相互调用跑完所有测试及其子测试。

这个逻辑还是比较简单的，其他的配置准备逻辑，资源清理逻辑和并发同步逻辑，可以自行阅读理解，这里不做展开。

这里想进一步介绍的是 testify 基于 testing 套件实现的测试套件 Suite 的逻辑。

JUnit 组织测试的时候，由于 Java 天生按照类来组织代码，所以类自然而然的就成为了 Suite 的投影。然而 Golang 的代码却是按照 package 来组织的，这个粒度对于测试来说还是太粗了。因此 testify 或者 pingcap/check 都是自己组织了一套 Suite 逻辑来进一步细分同一个 package 下的测试。

testify 驱动 Suite 运行的核心逻辑在 `func Run(t *testing.T, suite TestingSuite)` 这个函数，样例用法如下。

```go
type ExampleTestSuite struct {
	suite.Suite
}

func TestExampleTestSuite(t *testing.T) {
	suite.Run(t, new(ExampleTestSuite))
}

func (s ExampleTestSuite) TestSimple() {
	s.True(true)
}
```

可以看到，驱动 Suite 的源头还是 testing 套件，testing 调用 `TestExampleTestSuite` 函数，再调用 `suite.Run` 执行 Suite 的驱动逻辑。

在这个 Run 函数里，通过反射和字符串匹配找到 Suite 的方法里形如 `TestXxx` 的测试函数，并装配好测试运行的逻辑，随后打包迭代地调用 `t.Run` 执行。不同于 testing 提供的基础逻辑，在装配过程中 testify 提供了更丰富的 hook 点，例如 Setup/TearDownSuite 和 Setup/TearDownTest 等。

这就是测试套件背后的秘密，并不是你定义的 `TestXxx` 函数或者 Setup/TearDown 系列方法有什么魔力，只是测试驱动逻辑在背后通过反射取出，并经由常规的编程手段装配好每个逻辑的调用点和调用顺序罢了。

在上面提到的测试迁移提案里，我用 Note 的方式标注了不要将 pingcap/check 的 Suite 套件迁移成 testify 的 Suite 套件，而是仅利用 testify 提供的丰富的断言来简化测试代码。这是为什么呢？

```go
// without testify assertions
if expected != actual {
    t.Fatalf("Expected: %v, Actual: %v", expected, actual)
}

// with testify assertions
require.Equal(t, expected, actual)
```

如上所示，testify 的断言能够简化代码，同时优化错误输出。但是 Suite 的实现却有两个明显的问题，一个是代码依赖的泄露，另一个是无法良好的协调并发测试功能。

前者是一个 coding taste 的问题，如果你为一个较重的测试编写了复杂的 Setup/TearDown 逻辑，而其他测试未必需要 Setup/TearDown 的全部逻辑，但是开发者出于方便或许会直接借用你的 Suite 来创建新的测试用例，这就导致了代码依赖泄露。也就是说，简单的测试用例依赖了复杂的测试套件。

后者则是一个缺陷，记录在 [testify/issues#187](https://github.com/stretchr/testify/issues/187) 上。如同我在 issue 上回复的一样，是下面这段代码有问题。

```go
test := testing.InternalTest{
  Name: method.Name,
  F: func(t *testing.T) {
    // ...
    defer func() {
      // ...
      suite.SetT(parentT)
      // ...
    }()
    // ...
    method.Func.Call([]reflect.Value{reflect.ValueOf(suite)})
  }
}
```

这里 `F` 函数会在实际驱动 Suite 运行的时候交给 `t.Run` 执行，在 `t.Run` 里，又会通过 `go tRunner(t, f)` 创建一个新的 goroutine 跑 `F` 函数的逻辑。通常来说，虽然新的 goroutine 会并发执行，但是下方又有一句 `if !<-t.signal` 来阻塞等待 `tRunner` 返回。如果你要并发运行测试，那么就需要在测试函数里调用 `t.Parallel()` 方法来提前发送信号解除阻塞。

testify Suite 并未提供并发运行的方法，所以想要并发测试，必须依赖现成的 `t.Parallel()` 方法。

```go
type ExampleTestSuite struct {
	suite.Suite
}

func TestExampleTestSuite(t *testing.T) {
	suite.Run(t, new(ExampleTestSuite))
}

func (s *ExampleTestSuite) TestSimple() {
	s.T().Parallel()
	s.True(true)
}

func (s *ExampleTestSuite) TestSimple2() {
	s.T().Parallel()
	s.True(false)
}
```

可以看到，TestSimple 用例应该通过，而 TestSimple2 用例应该失败。实际运行几次，你会发现 TestExampleTestSuite 总是被标记失败，因为它的子测试失败了，但是 TestSimple2 有时返回失败，有时返回成功，而不是一直返回失败。这就是出现了数据竞争的情况。

这个现象的根源在上面提到的有问题的代码块里，testify 通过反射找到测试用例后，调用方法执行测试逻辑，但这个测试逻辑的运行是在 `t.Run` 通过 `go tRunner(t, f)` 创建的 goroutine 里运行的，而重置 `s.T()` 结果的 `suite.SetT(parentT)` 在 defer 语句里，仅当这个 goroutine 退出时才会被调用。

testify Suite 先收集完所有的测试函数，再在一个循环里迭代调用 `t.Run(test.Name, test.F)` 运行。如前所述，如果是串行运行测试，每个测试互不并发，总是等待前一个测试用例结束后，通过 defer 语句重置 `s.T()` 再执行自己的逻辑。然而，如果是调用了 `s.T().Parallel()` 方法，那么 `t.Run` 将提前返回，驱动下一个测试用例。如果下一个测试用例运行中途，前一个并发测试完成，在 defer 语句里调用 `suite.SetT(parentT)` 方法，就会导致下一个测试用例的 `s.T()` 被替换成了另一个实例，从而导致被标记失败的 `testing.T` 对象有误。

上面只是最简单的一个错误例子，如果测试用例不断增加，测试逻辑更复杂，还会出现用例 A 的错使得应当通过的用例 B 报告失败的情况。

总的来说，这是一个典型的并发修改全局变量而未处理好临界区的案例。一种解决方法是类似 ThreadLocal 变量的思路，为每一个 `F` 函数创建一个本地副本。这也是 [testify#1109](https://github.com/stretchr/testify/pull/1109) 的解决思路。

但是，鉴于 testify 在设计 Suite 的时候并未考虑到并发测试的问题，我还是谨慎地选择避开使用它以免之后被这些问题困扰。

虽然经常嘲讽 Golang 大道至简智力减半，不过它在测试上的考量经过这么些年的发展也是比较完整的了。推荐各位读者都读一读 [testing 的文档](https://pkg.go.dev/testing)，有些设计还是值得记下来的。

这里挑两个跟并发测试相关的点讲讲。

一个是 `t.Parallel` 能够标记一个测试是并发测试，并且不阻塞调用该测试用例的函数使其可以继续驱动下一个测试用例。这样看，似乎并发测试有如脱缰野马随时会运行。其实不然。testing 通过跟 `t.Parallel` 的函数的调用者绑定的 barrier 等一系列同步手段，保证并发测试只跟并发测试一起运行，串行测试单独串行运行，期间不会有并发测试运行，从而保证了基础的并发边界。

pingcap/check 当中，Suite 内部是串行的，不同 Suite 之间是并发的。所有 SerialSuite 会在所有 Suite 执行结束后，最后串行执行。testing 大体相仿，只不过 Suite 和 SerialSuite 换成了并发测试用例和串行测试用例，以及串行测试用例未必最后执行，可能在任何时候被调起，只是此时不会有任何并发测试运行。

另一个是 `t.Run` 与 Suite 和并发的关系，文档上提供了这么两个用例。

```go
func TestTeardownParallel(t *testing.T) {
    // This Run will not return until the parallel tests finish.
    t.Run("group", func(t *testing.T) {
        t.Run("Test1", parallelTest1)
        t.Run("Test2", parallelTest2)
        t.Run("Test3", parallelTest3)
    })
    // <tear-down code>
}

func TestGroupedParallel(t *testing.T) {
    for _, tc := range tests {
        tc := tc // capture range variable
        t.Run(tc.Name, func(t *testing.T) {
            t.Parallel()
            ...
        })
    }
}
```

第一个比较直白，就是需要 Setup/TearDown Suite 式的逻辑的时候，可以通过手动装配测试与子测试来达成。

第二个跟并发相关，可以通过子测试来组织并发测试。这里面有两个要点，一个是在所有并发子测试完成之后，上级测试才报告完成。另一个是如果上级测试不是并发测试，那么并发子测试就仅在相互之间会并发执行，不会跟其他任何测试并发执行。其实，如果追溯到 `tRunner` 的调用者 `runTests` 函数，你就会发现测试的最外层就是一个 `testing.T` 来驱动的，所有的测试用例就是它的子测试。

合理用好子测试的抽象，协同好并发，抽取出 Setup/TearDown 逻辑，就可以组合出你想要的测试逻辑。这才是软件开发应该追求的境界，组合正交的基础元素来得到复杂的应用逻辑。

关于测试的方面就讲到这里，最核心的内容是测试框架的组成成分分三种，Runner 驱动测试执行，测试函数即测试用例本身，以及 Runner 在驱动测试执行的过程中提供的 hook 点。关于 Golang 测试框架的介绍只是一个实例分析，其他语言及其测试框架各有各的特点。

哪怕是 Golang 测试的介绍，本文也不算详尽，因为缺少了测试二进制编译和链接的许多细节。Golang 的学习材料，我觉得大部分书籍都不如官方文档来得详尽，要想做到精通还是要从实践入手。

如果想要了解 Golang 的设计原理，其实要考虑到 Golang 的设计者是 C 专家出身，开发过 Plan 9 操作系统，得多看看这方面的材料才行。

例如，Plan 9 的经典设计就是它扩展“一切都是文件”这个概念，把进程和网络都深深地跟文件系统抽象结合起来，用这种视角看待 goroutine 和 net/rpc 库，应该会看到不一样的东西。

例如，毫不客气的说，Golang 可以说是现代的 C 语言，虽然多了运行时和语法差异，但是链接和装载那些问题，Golang 一个没屏蔽掉。要想了解 Golang 在编译阶段干了什么，难缠的符号解析问题怎么排查，建议读一读这本[《程序员的自我修养》](https://book.douban.com/subject/3652388/)。不要被它的书名给骗了，副标题“链接、装载与库”才是真相。

关于测试的内容，再补充一篇阅读材料[《测试的道理》](https://www.yinwang.org/blog-cn/2016/09/14/tests)，以作为强调测试的相反观点补充。软件开发没有银弹，多数时候你是在不同的选择之间做权衡。测试也是一样，对于大多数学生来说，测试被过度忽略了，但是狂热的崇拜测试，也不必要。

本来还有两个话题想讲，但一不留神就写多了，再写就远超一篇文章的体量，所以就此打住，待日后再续写。

各位可以猜一下另外两个容易被学生或是职场新人忽略的组成高质量软件的重要部分是什么。给个提示，程序的 1/3 是功能代码，另外 2/3 是什么呢？

最后，欢迎参与 TiDB 的测试迁移工作，一起创造一个优秀的分布式数据库。

https://github.com/pingcap/tidb/issues/26022
