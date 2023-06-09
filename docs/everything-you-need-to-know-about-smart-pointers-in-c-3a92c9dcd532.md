# 关于 C++中的智能指针，你需要知道的一切

> 原文：<https://medium.com/codex/everything-you-need-to-know-about-smart-pointers-in-c-3a92c9dcd532?source=collection_archive---------6----------------------->

C++中的智能指针提供了一种更安全、更简洁的操作指针的方式。它们省去了所有麻烦，例如，由内存泄漏和悬空指针引起的麻烦。

本文从理论和实践的角度介绍了智能指针:

*   它介绍了标准库中可用的三个智能指针类，并向您展示了如何使用它们；
*   它展示了如何从头开始实现其中两个类的简单版本，以便您能够理解底层机制。

![](img/bbadb8fd294833ea8afac7851a8b14a0.png)

罗宾·沃拉尔在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 总体想法和动机

当在 C++程序中动态分配内存时，我们需要手动释放它，通常使用关键字`delete`:

该程序显示:

```
Oh hello! I am X!
I'm dying…
```

第一行由指令行 20 打印，第二行由指令行 21 打印。

不得不释放动态分配的内存块会导致一些问题。特别是:

*   我们可能忘记删除指针，导致内存泄漏。
*   这可能会使程序变得异常安全更加困难。例如，如果`saySomething`或`MyClass`的构造函数抛出异常，那么`delete`语句行 21 将不会被执行，并且`MyClass`的析构函数也不会被调用，导致内存泄漏和潜在的更严重的后果。

如果`myClass`没有被动态分配，那么当对象超出范围时，析构函数将被自动调用。智能指针的主要目标之一是将这种行为扩展到指针:*智能指针是指针的包装器，它提供了自动内存管理等功能。*

他们使用操作符重载来模仿常规指针操作的语法，比如`*`和`->`。

标准库提供了三个智能指针类:`unique_ptr`、`shared_ptr`和`weak_ptr`。

# 唯一指针

类`unique_ptr`是 C++中最简单的智能指针。关于他们，你需要知道两件事。

*   一旦它们超出范围，就会被自动删除。我们称这样的指针为“作用域指针”。因此，当我们想在有限的范围内引用动态分配的对象时，它们特别有用。
*   你不能复制它们(因此限定词*唯一*)。

这两个点是相连的:如果你有一个作用域指针`y`的副本`x`，那么当`y`超出作用域时，`x`和`y`都指向的内存块被释放。`y`会因此变成悬空指针。

# 唯一指针不能做的事情

正如我们刚才所说的，有两种操作不能用唯一指针执行:复制和赋值。下面的程序显示了可能导致错误的两个操作:

如果您需要移动一个唯一指针并将其传递给另一个函数，您可能需要使用标准库函数`move`，如下例所示:

使用`move`后，`ptr`成为空指针:你将所指向的块`ptr`的所有权从`ptr`转移到`bar`。

# 例子

让我们回到前面给出的例子。首先，我们需要在文件顶部包含`memory`头:

```
#include <memory>
```

然后我们将修改`main`函数，使其看起来像这样:

我们使用`std::make_unique`创建一个唯一的指针。它将参数序列传递给`MyClass`的构造函数。然后，我们可以使用箭头操作符来访问对象的属性和方法，就像我们处理常规指针一样。

上面的代码打印了下面两行:

```
Oh hello! I am X!
I'm dying…
```

如您所见，当我们超出作用域时，析构函数被调用，这意味着存储`MyClass`实例的内存块确实已经被自动释放。

智能指针也适用于基本类型:

这会产生以下输出:

```
0x7fc6d3405b40
1
```

第一行表示指针的内存地址。第二行指示它所指向的值。

## 从头开始实现唯一指针

我们将创建一个名为`MiniUniquePointer`的泛型类，并依赖于类型`T`。它将存储类型为`T*`的指针`mPtr`和以下方法:

*   构造函数接受一个类型为`T*`的参数并将其赋给`mPtr`，
*   析构函数，删除`mPtr`，
*   `operator*`和`operator->`对应的是常规指针操作符。`operator*`返回对`mPtr`(即`*mPtr`)后面的值的引用，`operator->`返回`mPtr`本身。

下面是实现过程:

除了定义我们上面描述的四个方法之外，我们还显式删除了复制构造函数和赋值操作符，以防止用户复制。

然后我们实例化并使用`MiniUniquePointer`,如下所示:

# 共享指针

C++中存在的第二种智能指针是*共享指针*。共享指针可以被复制，并且它们所指向的内存块不会被释放，直到指向它的所有其他共享指针都被析构。当一个共享指针被实例化时，一个额外的内存块被分配。它被称为*控制块*，记录已经复印的份数。引用计数器一达到 0，共享指针指向的对象就被删除，也就是说，当最后一个剩余副本被销毁或被分配另一个指针时。

这个额外的功能是以较大的开销为代价的，所以当一个唯一的指针足够用时，不应该使用共享指针。

# 例子

正如我们对唯一指针所做的那样，我们通过将类的构造函数的参数传递给函数`std::make_shared`来创建共享指针:

就像使用唯一指针一样，我们可以使用`->`访问`MyClass`的相应实例的成员，当`main`函数终止时，它占用的内存块被释放。然而，我们现在可以制作`sharedPtr`的新副本，并在多个范围内共享它们:

如果我们运行上面的程序，我们将得到以下输出:

```
From main Oh hello! I am X!
From hello Oh hello! I am X!
Back in main
I'm dying…
```

正如我们所见——正如我们所料——一旦主函数终止，那么`sharedPtr`和`localPtr`所指向的`MyClass`的实例就会被删除。`localPtr`之前出作用域了，但是引用计数器记得`sharedPtr`可能还需要用。

# 履行

我们将从创建一个负责统计引用的类`ControlBlock`开始。它将有一个类型为`int`的属性`mReferenceCount`和两个分别递增和递减`mReferenceCount`的方法`add`和`remove`。实现非常简单:

需要注意的一点是:我们对添加一个新引用后的引用数量不感兴趣，但是我们需要检查在删除一个引用后它是否达到了零。这就是为什么`add`和`remove`的返回类型不同。

核心`MiniSharedPointer`类的结构与`MiniUniquePointer`非常相似。然而，我们需要存储一个指向控制块(`mControlBlock`)的指针，我们实现这些方法的方式有很多不同:

*   构造函数除了存储指针之外还实例化新的控制块，
*   析构函数告诉控制块一个引用已经被移除，并且只有当引用计数器达到零时才删除指针(并释放控制块),
*   复制构造器递增引用计数器并将`mControlBlock`和`mPtr`的值从现有实例复制到正在构造的实例，
*   赋值操作符递减左边的引用计数器，如果它达到零，就执行适当的清除，然后做同样的事情，就好像我们调用复制构造函数将左边复制到右边一样。

我们按如下方式实现它:

# 处理悬空指针和循环依赖

我们讨论的最后一种智能指针是*弱指针*。弱指针类似于共享指针，只是它们没有控制块和引用计数器。这意味着您可以共享它们，但是它们指向的对象可能会在它们超出范围或被分配另一个指针之前被销毁。

您需要知道两种操作弱指针的方法:

*   `expired`:它不接受参数，返回`true`它所指向的内存块已经被释放，`false`否则；
*   `lock`:不接受参数，返回`expired() ? shared_pointer<T>() : shared_pointer(*this)`。这是一种“安全的取消引用”方法，因为它能够在检查内存块是否已被释放后获取内存块的值。

下面的例子展示了它们的行为:

以下是输出:

```
I'm dying…
weakPtr points to a deallocated block
```

`sharedPtr`超出范围(第 8 行)。它所指向的内存块随后被释放，即使`weakPtr`仍然持有对它的引用。因此，`weakPtr.lock()`返回一个空的共享指针，并且不满足第 11 行的条件。

弱指针有两个主要优点:

*   它们防止由悬空指针引起的错误:通过提供一种方法来检查它们所指向的块是否已经被释放，它们防止用户取消引用和操作悬空指针。
*   它们解决了循环依赖问题。例如，如果您运行以下代码:

那么`a`和`b`都不会被析构:只要`a`还活着，就不能析构`b`，因为`a`包含对`b`的引用，同样，`a`也不能被析构，因为`b`包含对它的引用。这会导致内存泄漏。

为了避免这个问题，我们可以简单地将`B`和`A`的属性`a`和`b`的类型从`shared_ptr`改为`weak_ptr`。

# 参考资料:

[在 C++中实现简单的智能指针](https://www.codeproject.com/Articles/15351/Implementing-a-simple-smart-pointer-in-c)

[https://www.youtube.com/watch?v=UOB7-B2MfwA&list = pllratfbnz 98 dudn 48 yfguldqgd 0s 4 FFB&index = 44](https://www.youtube.com/watch?v=UOB7-B2MfwA&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=44)

【http://ootips.org/yonat/4dev/smart-pointers.html】

[https://iamsorush.com/posts/weak-pointer-cpp/](https://iamsorush.com/posts/weak-pointer-cpp/)

[在现代 C++中将智能指针移入和移出函数](https://www.internalpointers.com/post/move-smart-pointers-and-out-functions-modern-c)