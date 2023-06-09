# 但是人工智能到底是什么？

> 原文：<https://medium.com/codex/but-what-is-artificial-intelligence-exactly-c1acbe3c3cd1?source=collection_archive---------6----------------------->

# 开始

这是一个关于我尝试神经网络的故事。

旅程就像许多其他故事一样开始了:在 YouTube 上，当你无聊的时候。我不知道你的 YouTube 主页，但我的主页是*奇特的*，充斥着许多数学相关频道的随机短视频、丑陋的模因和数学视频。有一天，算法给了我一段视频，这段视频引起了我的注意:

该视频展示了一个所谓的“*神经网络*的实现，它代表了 chrome dino 的大脑，随着时间的推移，dino *通过*学习* *其环境*来学习*如何避开障碍物。这个概念，对我来说，至少可以说是惊人的:我编程已经有一段时间了，但我一生中从未见过这样的事情。真的能*给一堆数字教*点东西吗？在这种背景下怎么谈*学习*？“神经网络”到底是什么？

所以我立刻知道我要如何度过这一天，在 YouTube 上搜索其他视频，更详细地解释恐龙大脑中发生的事情。

# 神经…什么？

基本上，除非你一直生活在岩石下，否则你可能已经注意到人工智能现在就在我们周围，许多公司正在实施这种算法，可以越来越好地解释他们从我们这里收集的数据。在很大程度上，这些算法只不过是“神经网络”:让我给你看一个小图来说明我们正在谈论的内容，即使你可能在其他文章中在线看过这个图。

但是，首先，术语“神经网络”意味着我们正在处理某种“神经元”的“网络”，如果你仔细想想，大脑是如何工作的(*我不是生物学家，但你明白这一点*)。

![](img/7e92bb2f3a21347af06f73aa6ce9c850.png)

一张神经元的图片，是我从维基百科[上偷来的](https://it.m.wikipedia.org/wiki/File:Neuron.svg)。

假设一个神经元可以很容易地用两部分来表示，一个**圆**，现在我称之为*头*，一个**线**，尾*尾*。因此，这种神经元的网络看起来就像我从维基百科上偷来的这张图片一样(*顺便说一下，和神经元*一模一样):

![](img/cb0cc2ad7f142f3487d1fbcfa9ef5df4.png)

一张神经网络模型的图，这也是我从 [*维基百科*](https://it.m.wikipedia.org/wiki/File:Neural_network.svg) *偷来的。*

我知道，这看起来令人生畏，但这是一个神经网络的相当好的代表；正如箭头所示，这个图有一个方向，事实上我们通常做的是*将*神经网络输入绿点(左边)，并从黄点(右边)获得最终输出。这个图表还表明*神经元*的数量完全是任意的:输入的数量，输出的数量，甚至那些我们还没有谈到的在中心的怪异蓝点的数量。但在此之前，我们需要介绍这个*机器学习*世界中的另一个非常重要的术语，*层*:如果你仔细观察，这个图在某种程度上被分为三个垂直部分，由神经元列定义:这些是我们小型神经网络的*层*。我们可以得出的结论是，像这样的网络肯定有一个**输入层**和一个**输出层**，中间一列通常被称为**隐藏层**(通常网络的*深度*不止一个单独的隐藏层)。

正如我们的直觉所暗示的，大脑的这种粗略表示必须与某种数学概念相匹配，否则整个网络只不过是一幅奇怪的图画。而实际上，这个*是*一个数学模型的绘图，它能够*通过微调和调整其参数来学习*。

# 是的，那很酷…但是实际上呢？

现在是旅程中最乏味的部分，我们需要一些先验知识来理解我将要展示的公式背后的思想。特别是，我们在讨论中需要的数学分支主要是线性代数，老实说，这是我目前正在研究的课题。但是在这篇文章中，我想尽可能保持事情的直观性，*所以让我们来看看公式，好吗*？

![](img/25aefb277df5c53197bb1119a5b87db9.png)

神经网络的超级简单公式。

就这么简单。

我知道你在想什么，这是一个像“*那个*和“*到底是什么”这样的东西，迅速升级，起初我以为我可以在没有任何先验知识的情况下阅读这篇文章*。老实说，这个确切的公式只是表达这样一个事实的一种方式，即神经网络真正做的是**将一些值**作为输入(我们称之为*输入向量* ), ***多次变换*这些值**通过隐藏层(用函数的组合来表示)，并且**返回这些变换的结果**。一旦你理解了这个想法，你就知道我们真正感兴趣的是**如何**转换输入值以获得期望的输出值。

为了使事情变得简单，假设您有一个 2D 点的集合，并且您想要找到能够描述 *x* 值和 *y* 值之间关系的最佳直线。例如，假设我们有这些数字:

```
[(-2, 5), (3, 7), (6, 8.2), (-10, 1.8), (-5, 3.8)]
```

> 正如我们在学校所学的，假设我们需要找到一条线，我们知道我们只需要 2 个点，因为对于 2 个点，只有一条线可以同时穿过它们；但是，为了这个实验，我们需要的不仅仅是 2 个点，稍后你会明白为什么。

好吧，那我们从哪里开始？一条线基本上由两个数字表示，系数——表示线的斜率——和 *y-* 截距——告诉我们曲线的“高度”。学校还告诉我们，有一个简单的等式，我们可以从中推导出这两个数字，但这不是一个非常通用的解决方案，因为我们想做的是确定一个**通用**算法，它可以做得比仅仅是线条更好(因为你必须承认，*线条很无聊*，而且这个世界比仅仅是线性关系更复杂)。

我们试试另一个思路:假设解是`y = 3.6x + 5.2`，方程中有两个随机数。现在，让我们检查我们是否错了，例如通过插入第一个点的 *x* 坐标，我们得到

```
3.6 * (-2) + 5.2 = -2
```

也就是*肯定不是* `5`，所以我们知道我们的线是不正确的(*谁会想到，通过扔随机数，你得不到正确的解*)。这个结果当然不会让我们吃惊，但是我们想评估一下*我们错了*多少:期望值是`5`，但是我们得到了`-2`，所以我们错了`5-(-2) = 7`个单位。我们如何调整我们的线的参数，以匹配精确的答案呢？事实上，这个问题的完整答案超出了本文的范围，所以我们要用我用来训练我的神经网络的算法来做这件事，这个算法被称为“**随机搜索**”。

这个想法相当简单:对你的解决方案进行一些随机调整，评估每一个调整的错误程度，然后选择最好的一个——一遍又一遍地重复这个过程，直到解决方案足够好。听起来很合理，你不觉得吗？

但是我们遗漏了重要的一步，你如何选择最佳的调整？下面我们来介绍一下*成本函数*:

![](img/dfef4b1ecfd17f662d005445332168f2.png)

用于评估平均成本的公式。

这是另一个表达简单概念的难看公式。这个公式说的是**计算输出层和期望输出**之间的差的平方和，并将结果除以输出的数量(这意味着我们正在评估*平均成本*)。而且你想想，我们只是手动做了这个算法的第一步，有了`7`的结果，除了我们没有求差的平方，那为什么那里有个平方呢？

我们通常因为两个原因来平方差异:第一个是我们想要将误差解释为与正确值的*距离，因此总是有一个肯定的答案更有意义(也因为我们正在评估平均值)；但你可能会问“*只使用绝对值，然后再使用*”，你可能是对的，但在这个例子中，我们对*求平方，给予更大的误差*更大的重要性，因为误差越大，平方越高。*

因此，让我们编写一个简单的 Python 脚本来处理手工计算平均成本的麻烦:

![](img/7c105091b90f155b9164a821c0479a18.png)

计算平均成本的小 Python 代码。

我们可以看到，结果并不是很好:其实数字越低误差越低，`362.856`绝对不是我们能去的最低。

为了最小化错误，我们需要稍微修改一下我们的代码，因为我们需要多次进行随机调整，直到我们对得到的解决方案满意为止。

小 Python 代码来近似给定数据集中的任何线。

> 这段代码包括了一些我们还没有谈到的小细节:首先，`40_000`是“epochs”的个数，它代表了我们基本上调整了我们的近似值多少次(试着改变这个数，看看会发生什么)；第二，我们在没有标准的`random` Python 库的情况下生成随机值，原因是我们需要每一个调整都有相等的可能性被选取，这可以通过从正态分布返回样本来实现，以`0`为中心，以`1`为标准偏差；第三，`STEP_SIZE`是一个乘法常数，它定义了产生的调整应该有多大。顺便故意省略了结果，自己去查，我觉得满意多了。

# 我们在谈什么？

但是所有这些与我们之前讨论的“神经网络”有什么关系呢？嗯，实际上，神经网络并不比这个小例子更特殊，除了它们能够**逼近非线性函数**，并且它们并不局限于 2D，事实上它们通常解决具有**十亿维复杂性**的问题。以 *MNIST 数据集*为例:如果你从未听说过这个数据集，它只是大量手写数字的图片，与相应的数字相关联。由此，你可以建立自己的神经网络，能够识别手写数字！

现在，让我们更深入地了解一下我在过去几天里都做了些什么。你听说过 [Rust 编程语言](https://www.rust-lang.org/it)吗？如果你还没有，不要担心，神最终会带你走上正确的道路。Rust 可能是唯一一种完全改变了我编写和思考代码设计方式的编程语言，如果你不知道在业余时间做什么，去看看吧！无论如何，这不是一门简单的语言。但是这很棒，相信我，不仅仅是 rust 本身，而是整个 Rust 生态系统，还有这个社区都很棒——这是一个非常重要的细节。

这个 Rust 的赞美只是介绍我这个星期一直在做的事情的一种方式，这基本上是一个从头开始的**神经网络**——*因为这就是“Rustaceans”所做的*。这是我用来做实验的所有代码的储存库。

[](https://github.com/ph04/random_search) [## GitHub - ph04/random_search:一个神经网络模型，可以通过…

### 一个神经网络模型，可以近似任何非线性函数，使用随机搜索算法为…

github.com](https://github.com/ph04/random_search) 

> **对于书呆子**:通常神经网络的计算是在适当的硬件上进行的，以更快地处理数据，如 GPU 或谷歌的 TPUs 相反，我们正在用我们的 CPU 计算矩阵乘法，因为我们是哑巴，也因为 GPU 代码是愚蠢的困难——如果你需要好的结果，你需要他们快，在线租一些 GPU，不要打扰我。此外，如果您决定在您的机器上运行这段代码，请注意，CPU 可能会变得**非常热**(74℃)，这取决于您选择的超参数和您想要近似的函数，因为我用来并行执行计算的库使用了所有可用的 CPU(如果您愿意，您可以改变这种行为，但我不知道如何改变，因为我对此太厌烦了)。

基本上，所有相关的代码都在这里:

![](img/09edfc01178ae1070f3ebe0f04819be7.png)

实际的相关代码。

这是执行我们之前谈到的*转换*的代码，我们还有另一个非常重要的代码片段:

![](img/619e90f8cd6956ccfd4615aa4c0b8627.png)

实际-实际相关代码。

顾名思义，它执行随机搜索，优化网络参数。

> **对于书呆子来说，还是**:这段代码与我们之前的 Python 例子有些不同，因为为了加快计算速度，我生成了随机种子，而不是直接随机调整，然后我根据给定的种子评估了相应的调整，然后在计算出哪些调整给出了最小的平均成本后，重新构建了最佳调整。
> 
> 如果你不明白，再读一遍这个句子，最终会明白的。

…但是，等等，我们在这里优化的是什么参数？在我们之前解释的图表中没有“T8”系数“T9”这种东西，那么我们还在谈论什么呢？

# 这里需要调整的参数是什么？

你还记得文章开头的那张图片吗，展示了奇怪的线条和圆圈迷宫？现在，我想让你想象*那幅图* **中的每一个圆圈和线条都代表一个数字**——这是一个可以想象的数字。一个随机数，对于模型的每个组成部分，这就是我们初始化神经网络的方式，就像我们对我们的线所做的一样。我们如何计算事物？

**警告** : *这将变得更加专业，但是如果你已经做到这一步，你已经对这个讨论有了一个不错的想法——如果你想跳过这一部分，你可以继续，但是我建议花一点时间来理解这一段的核心思想，因为它肯定是整篇文章中最重要的部分。*

每一层不过是一个**向量**，每一层之间的*尾-* 迷宫就是一个**矩阵**，线性代数就是从这里出现的。现在让我们在这里添加一些适当的术语:每个圆圈代表每个神经元的**偏差**——你可以将其解释为一条*多维曲线*的*y*——截距——每条线代表一个**权重**，因为为了评估事物，我们现在必须处理**矩阵乘法**，因此这个矩阵*为每个输入赋予一个权重*(并且还改变向量的大小)。

所以，要从那个东西里得到一些数字，做这些步骤:

*   将您的输入输入到绿点中
*   将输入向量乘以权重矩阵，得到与蓝色隐藏层大小相同的向量
*   添加隐藏层的偏差
*   *应用非线性函数*
*   重复此过程，直到到达网络的末端

![](img/0aff65e7dec407a1da6232bec4cba4fa.png)

网络的一步。

再看一遍文章开头的这段公式，因为现在它应该有意义了！很简单，对吧？

…但是等等，那第四步呢？看到那个符号了吗？那就是**非线性函数**，也就是通常所说的*激活函数* : 它的目的是让神经网络学习非线性函数，粗略地说——*如果你要专业的话，“仿射变换的合成仍然是仿射的”，这样网络就无法学习非线性函数*。

# 最终结果

让我们看看 Rust 计划的一些结果:

![](img/92fb53fc59bc059285d8220af5fd7062.png)

sin(x)从-5.0 到 5.0 的近似值。

是不是很神奇？这个呢:

![](img/8e1bba44a228bd3e4026fa1cc394f385.png)

sin(2x) + x 从-5.0 到 5.0 的近似值。

我认为结果是不言而喻的——特别是在这些例子中，我使用了由 32 个神经元组成的 3 个隐藏层的网络。

# 结论

就这样，我希望我提高了你对这个美丽领域的兴趣，这个领域将**数学**和**计算机科学** *完美地结合在一起*。正如我所说的，我仍在学习很多东西，但我认为没有什么比得上当你能够将 T42 理论告诉你的东西付诸实践的感觉。我花了很多时间来修复我的 Rust 代码中的许多错误，但最终我们在 Desmos 上绘制了这些惊人的曲线。

最后，*但绝对不是最不重要的*，**巨大的**感谢 Modesti Dennis，他在这个旅程的每一步都帮助了我，他比我知道更多与数学相关的东西。同时，感谢他向我介绍了 Rust 编程语言，并教会我如何用不同的方式处理事情。

# 如果你真的对这方面的细节感兴趣…

这是故事的结尾，但我想列出我在编写 Rust 代码时遇到的一些 bug，所以如果你试图从头编写一个神经网络，并且平均成本没有降低，请首先检查这些东西:

*   不要构建整个库来做一个实验，这是愚蠢的，因为不可避免地，更多的代码=更多的错误(T2)
*   检查您是否正在评估初始值*和*的**和**的平均成本，以及**而不是**单独的调整成本，否则不要期望代码能很快工作
*   确保使用正态分布生成随机调整，因为调整在每个方向上的概率必须相等
*   确保网络有一个**合适的大小**:这部分非常重要，这个问题的答案完全是经验性的，你需要摆弄参数，最终你会找到你的问题的最佳参数
*   除非你知道自己在做什么，否则不要下任何结论

在储存库的`README.md`中，我留下了一些实验的结果以供参考。