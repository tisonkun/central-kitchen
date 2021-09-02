---
title: '夜天之书 #9 Sneaky Throw'
---

确实只有编号的标题表意比较弱，虽然我不起标题以后产量大幅上升，但是本来也会写摘要，摘要拿一点放到标题里也不是不行。

今天时间有限，复刻一篇旧闻，讲的是跟错误处理相关的，算是为之前埋下的错误处理伏笔开个头。

几年前在读 Hazelcat Jet 代码的时候看到了这么一段。

```java
@SuppressWarnings("unchecked")
public static <T extends Throwable> RuntimeException sneakyThrow(Throwable t) throws T {
  throw (T) t;
}
```

这个实用函数可以在实际编写代码的时候，像下面这样绕过 Java 编译器检查 checked 异常在签名中的要求。

```java
@Override
public void close() {
  if (state == CLOSE) {
    try {
      closeFuture.get();
    } catch (Exception e) {
      throw sneakyThrow(e);
    }
  } else if (state != END) {
    closeProcessor();
  }
}
```

我们实际抛出了异常，并且 close 方法并未标注 throws Exception 信息，可是编译仍然通过了。

更重要的是，运行时如果进入到异常路径，抛出的也是原始的异常，而不像常见的用 new RuntimeException(e) 包装的绕过手段，会变成 RuntimeException 在最外层。

这是为什么呢？我们先做几个实验。

```java
public static void main(String[] args) {
   sneakyThrow(new Exception());
}

// 1
private static <T extends Throwable> void sneakyThrow(Throwable t) throws T {
  throw (T) t;
}

// 2
private static <T extends Throwable> void sneakyThrow(T t) throws T {
  throw (T) t;
}

// 3
private static <T extends RuntimeException> void sneakyThrow(Throwable t) throws T {
  throw (T) t;
}

// 4
private static <T extends IOException> void sneakyThrow(Throwable t) throws T {
  throw (T) t;
}
```

在上面的三个例子中，1 在运行时抛出 Exception 异常，2 提示没有处理 Exception 异常，3 在运行时抛出无法 cast 成 RuntimeException 异常，4 提示没有处理 IOException 异常。

这里的主要矛盾点有两个，第一个是方法签名中的 throws T 如何推断，第二个是 (T) t 强制类型转换如何发生。我们分开来讲。

对于编译器来说，是否要求 sneakyThrow 的调用点检查异常，取决于 throws T 中的 T 被推断为什么类型。

在 1 和 3 中，T 只出现在 throws T 中，T extends Throwable 是唯一的约束。在 sneakyThrow 的调用点上，Exception 参数被 cast 成 Throwable 类型。由子类转换成父类是个必定成功的动作，而此动作也不会影响 T 的类型推断。因此对于 T 的类型推断，实际上只有 T extends Throwable 一个约束。在这种情况下对 T 的推断在 Java 8 之后有明确的[语言规范](https://docs.oracle.com/javase/specs/jls/se8/html/jls-18.html)来限制。

18.1.3 Bounds 一节中提到

> A bound of the form `throws α` is purely informational: it directs resolution to optimize the instantiation of α so that, if possible, it is not a checked exception type.

而在 18.4 Resolution 一节中提到

> ... Otherwise, if the bound set contains `throws αi`, and the proper upper bounds of αi are, at most, `Exception`, `Throwable`, and `Object`, then Ti = `RuntimeException`.

简单地说，抛出的异常会被尽可能的推断为一个非 checked 的异常。

1 和 3 中，T 在调用点没有实际的类型约束，通过 extends 施加的类型约束属于规范中的范围。这种情况下，T 会被推断成 RuntimeException 类型。

2 中 T 被实参限制为 Exception 类型，4 中 T 的类型约束 T extends IOException 不属于规范中的范围，这两种情况下 T 分别被推断为 Exception 和 IOException 类型，因此编译器分别报出异常。

这是 Java 8 中一个有意为之的特性，具体的讨论可以参考[邮件列表的讨论](http://mail.openjdk.java.net/pipermail/lambda-dev/2013-February/007981.html)和 [StackOverflow 的讨论](https://stackoverflow.com/questions/31316581/a-peculiar-feature-of-exception-type-inference-in-java-8)。

第二个问题，(T) t 强制类型转换如何发生，这个也是编译器编译逻辑相关的问题。这个问题只跟 1 和 3 有关。

1 的例子里，Throwable 类型的变量 t 被作为 Throwable 类型的子类型 T 抛出。由于类型擦除的原因，在编译的时候编译器只知道 T 是 Throwable 的子类型，因此无法放置合适的类型转换，转换到自身类型或父类型是不需要任何 cast 的。

3 的例子里，编译器明确的知道抛出的是一个 RuntimeException 的子类型，而输入的是父类型 Throwable，因此可以推断出在 throw 之前可以放置 cast 到 RuntimeException 的类型转换。

最后，代码层面上还有一个小问题。Hazelcat Jet 的代码返回值是 RuntimeException 类型，而实验代码是 void 类型。这其中的差别在于你更喜欢写成 throw sneakyThrow(e) 的形式还是 sneakyThrow(e) 的形式。因为方法里面直接就抛异常了，理论上返回值类型写啥都行，只要能忽悠过编译器就可以。
