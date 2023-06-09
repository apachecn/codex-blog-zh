# 如何在 Python 3 中使用生成器

> 原文：<https://medium.com/codex/how-to-use-generators-in-python-3-b22a8df067a?source=collection_archive---------12----------------------->

![](img/b46342fe90eac33c95d18dadc389327e.png)

亚历山大·席默克在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

许多语言都有一个概念叫做迭代器；这些对象允许你迭代一些数据。Python 有一个叫做生成器的概念，它提供了一种构造迭代器的简单方法。我们将讨论生成器、迭代器和理解语法。这使得数据的构造和操作变得容易。

Python 中的生成器采用常规函数的形式。考虑以下两个函数，它们都创建一个数字列表:

第一个函数`func_fib`创建并返回从 1 到`high`的斐波那契数列。第二个也创建了斐波那契数列；然而，它并不简单地创建一个列表。第二个功能是生成器。

如果你调用`nums = func_fib(1000)`，所有的一千个号码都会被找到，放在一个列表中，列表会被返回。该列表将是`num`的值。但是，如果你调用`nums = gen_fib(1000)`，`nums`将简单地被分配一个生成器对象；不会计算任何数字。**这意味着对于像文件这样的大数据，使用生成器可以显著加快代码速度。这也意味着管理理论上无限数据的能力。**

使第二个函数成为生成器的唯一原因是使用了`yield`关键字。`yield`关键字的作用类似于`return`关键字，除了`return`停止函数执行。可以这样想:当您调用生成器函数时，它会创建一个生成器对象，其中包含这段代码，并复制粘贴了参数。然后，第一次迭代生成器时，代码将从头开始运行，直到找到一个收益。然后，它会输出一个数字。第二次迭代时，对象将从停止的地方重新开始。在这种情况下，将改变`x`和`y`的值，并再次检查回路状态。这种情况会一直发生，直到函数遇到`return`；要么由开发者放置以提前结束执行，要么在函数末尾隐式`return`。您实际上总是希望您的生成器包含某种包含`yield`语句的循环。

为了迭代一个生成器，您需要使用`next()`函数。当你通过做`nums = gen_fib(50)`创建一个`gen_fib`的实例时，你可以通过做`next(nums)`得到生成器的下一个值*。第一次这样做，你会得到 1。然后是 1、2、3、5、8、13、21 和 34。如果你再次做`next(nums)`，你将面临一个`StopIteration`错误。这给了你一个很好的方法来确定你是否已经到达了一个生成器的末尾。以下是如何使用`gen_fib`和`next`手动创建数字列表:*

这将起作用；然而，它显然是笨重的。因此，Python 包含理解语法。此语法适用于列表、集合和词典。对于其他类型，也有简单的方法将迭代器转换成那种类型。下面是理解语法如何与我们的`gen_fib`函数一起使用:

这个语法是 Python 中最有用的语法之一。它允许非常简洁地创建数据集。例如，在列表理解中，实际上涉及到两个生成器。我知道还有一种理解语法:生成器理解

这实际上是所有其他理解的工作方式；您创建一个生成器，它是另一个生成器的包装器。它实际上是一个压缩的`for`循环。您还可以执行以下操作:

您可以创建嵌套的`for`循环，可以使用`if`语句，并且可以从迭代器直接构造类型。这些只是使用这种语法的一些方法。然而，我建议你只在理解语法很小的时候使用它。如果您的代码变得不可读(并且难以维护)，那么您还不如使用一个循环。

您可能以前在 Python 中使用过生成器；`range`和`enumerate`是两种非常常用的发电机。如果你没有意识到，`enumerate`是一个和`range`非常相似的漂亮的生成器。下面两个代码段做同样的事情:

```
my_list = [1, 2, 3, 4]for i in range(len(my_list)):
    num = my_list[i]
    # Do stuff with num and imy_list = [1, 2, 3, 4]for i, num in enumerate(my_list):
    # Do stuff with num and i
```

让我们使用`range`创建`enumerate`来展示它是如何工作的:

`enumerate`简单地遍历数据并返回索引和该索引处数据的元组。`enumerate`唯一的问题是你不能直接控制开始或步骤。您*可以*使用切片来修改 iterable，但这并不顺利。因此，我创建了一个定制的`ascertain`函数，它充分利用了`range`的功能。

Python 的另一个有用的特性是`_`变量名。如果你用`_`代替变量名，意味着你不想创建一个变量。例如，以下代码块是等效的:

```
for i in range(len(iterable)):
```

和

```
for i, _ in enumerate(iterable):
```

如果想遍历整个 iterable，可以使用`enumerate`来避免使用`len`。生成器的另一个常见用途是文件读取；由`open()`创建的文件对象实际上是该文件的迭代器。如果为每个循环创建一个:`for letter in file:`，那么每次循环迭代时都会生成字母。如果您想一次读取所有文件，这对于大文件来说可能会有问题，您可以使用`file.readlines()`。Python 中的`in`关键字用于列表、生成器等可迭代数据类型。

Python 中的[迭代器](https://docs.python.org/3/library/itertools.html)有更多的**特性。希望您对生成器和迭代器有足够的了解，能够创建自己的生成器和迭代器，并使用 Python 内置代码中的生成器和迭代器。**