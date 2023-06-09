# 拥有特性，以及如何以有组织的方式交付

> 原文：<https://medium.com/codex/owning-features-and-how-to-deliver-in-an-organized-way-b8e81973a9e2?source=collection_archive---------16----------------------->

![](img/b7b5ac449408874c30118efb719079e0.png)

费德里科·贝卡里在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

在过去的许多年里，敏捷软件工程已经成为行业中的顶级工作方式，我们喜欢它。我们可以称之为冲刺或迭代，但任务是相同的——计划、交付、反思和重新开始。我们可以更快地交付，我们可以更快地进行编码，过程也更短，棒极了，对吧？那么，为什么有时候我们会觉得我们在 sprint 中“漂浮”,或者很多 sprint 过去了，我们却没有感觉到我们已经交付了我们想要的特性呢？

答案并不简单，因为它可能涉及许多影响团队如何交付的因素，但是我想关注的是，什么可以使我们，软件工程师，在敏捷设置中有效地和有组织地工作，并推动那些特性完成。

# **拥有它**

软件工程师职业发展的一个步骤是驱动和拥有特性。拥有一个特性意味着你(几乎)自始至终都处于主导地位，这伴随着大量的责任，但在我们选择实现它的方式上也有很大的自由。一个特性需要梳理，一个执行计划(我们将如何实现它)，测试和理解验收标准，最后部署和一些更多的验证测试。

特性所有权是软件工程师职业生涯中迈出的一大步，但也是一个学习的过程，路上会有一些颠簸。可以看到的一些颠簸如下:“拿了就消失”或“迷失在范围内”。

取而代之意味着只有一个人在实施，但是这个人没有分享任何关于实施方法的细节，或者可见的进展(在任何类型的敏捷板上)。它可能以一个非常长的代码审查结束，这将需要时间来完成。

迷失在作用域中意味着当我们的任务是从 A 到 B 时，我们要么被“C 呢？”或者“哦，我可能也应该做这个，这个和这个！”

我发现自己两样都在做。请记住，有一个学习曲线，因此，我想分享我的个人工具箱，以便在敏捷设置中高效工作(是的，拥有这些特性！)

重要的是要记住这是一个过程，一个花了我 3 年时间来掌握我的方法的过程，虽然不是所有的技巧在所有情况下都完美地工作，但这些仍然是我会与任何寻求掌握特性所有权的人分享的好技巧。

## **明确特性的范围——调整期望**

你是否曾经非常努力地开发一个功能，尽你最大的努力去交付，交付了这个功能，对此非常高兴，然后得到的反馈是:“这个功能还没有完成”…嗯，我有！当时，我对这个反馈感到非常难过，公平地说，给我的所有功能都没有任何描述…但这时我意识到，描述和调整期望非常重要，如果没有，我会确保有一个。

由于这个反馈，我执行的任何票据都有一个描述。故事或更大的任务不仅有描述，还有我们想要达到的目标，以及一些理想的接受标准。

保持期望一致的重要性不仅会使我们更有效率，还会确保我们交付正确的东西，并确定需要完成的工作的范围。这也将确保一个人对特性有正确的理解，并将减少在交付过多或过少的范围中迷失的可能性。

## 研究——为了加速而减速！

所以我们有了这个特性，我们是这个特性的所有者，太好了，现在让我们编码吧！嗯，没那么快…

这与特性描述有关，因为为了回答一些问题并写出我们需要研究的描述。通常，特性可能已经有了描述，问题是:我们完全理解它了吗？

研究进入领域，但也进入技术方面。

在研究领域时，我们需要确保我们理解我们期望从特性中得到什么，这可以通过提问、做笔记或写验收标准来完成。这个过程也将给出一个强有力的提示，告诉我们需要测试什么领域的功能，以确保结果是正确的。

通过对技术方面的研究，我们围绕如何实现这一目标产生了一个想法。有时，使用图表来描述我们正在探索的方面会有所帮助，而且还可以发现我们可能面临的任何一种明显的问题。一个很好的例子是绘制序列图，只需写下函数名，代码中调用这些函数的位置，以及调用这些函数的位置，人们可以找到缺失的集成，需要更多探索的功能，或者只是意识到某些部分可能需要更长的时间。

## **把事情分解成更小的任务**

分而治之。这是目前为止，我工具箱里最好的实践。

把事情分解成更小的任务，真正地收集前面几点中完成的所有工作，并把它变成可操作的项目。它表明执行特性的人有一个计划，了解他们需要解决什么，以及他们将如何实现它。

这是软件工程师真正有效的地方，因为从 A 到 B 的路不是在路上就能想出来的，但它更清楚如何到达那里，并且在范围内迷路的机会更少。

它不仅能让你看到事情的大小，还能看到事情的进展。如果这个人错过了每日会议，他们正在驾驶的功能的状态对每个人都是清楚的。

更小的任务意味着更小的可测试单元和更快的代码审查。

请记住，如果一个特性是由多人共同完成的，重要的是不仅要保持一致，还要对那些较小的任务进行描述。

注意 1——这种实践非常有用，但并不是我们所做的所有功能或任务都是相同的。记住，任务就是要有计划，而计划不一定要完美。通过尝试在不同的情况下使用这种方法，我们实际上可以改进我们的方法，并了解我们自己以及我们喜欢如何工作。

注意 2——当结对编程时，我们可以跳过分解，但是我强烈建议使用需要做的事情的清单。这有助于保持合作的正常进行，并知道在一个值得休息的时间后在哪里继续。

## **了解你的未知**

在软件开发中有未知是非常正常的，这就是为什么不可能完美地估计一些东西。通常我们会对我们所知道的东西有 70-80%的信心来开始执行，但是讨论和思考我们不知道的东西以及它会如何影响开发是很重要的。

一定要记下来，一出现这个问题就提出来，并试着想出解决这个问题的建议。

不是所有的未知都是可以解决的，但是记录它们和我们所做的假设/协议是有价值的。

## **受阻？不总是问题…**

那么，如果我们受阻会发生什么？这是可能发生的，在某些情况下可以解决，而在其他情况下我们只需要等待。

所以，让我们把注意力集中在我们能够解决的案例上，而不要只是等待我们能做些什么。

我遇到的最常见的原因是“API 没有准备好”的情况。在这种情况下，我们要么等待一个团队开发一个端点，要么用新的东西修改返回的响应，任何这些情况都可以通过一个非常简单的事情来解决:协作。

与团队保持一致，探索他们的合同，现在只是模拟它，如果就合同达成一致，或者至少在某种程度上，我们可以继续致力于该功能，由于测试，将模拟转换为“真实”系统应该不会太难。

这可以抽象为一个更大的想法:如果我被阻止了，我能做些什么吗，与谁结盟，以便并行工作？不要等待，如果合理的事情可以做，记住“围绕冲刺漂浮”，是的，这是其中一种情况。

关于这一点有一个重要的注意事项——如果一个系统被模仿，那么特性并没有“完成”,这意味着范围可能需要改变，并且应该进行后续任务。注意这一点，因为它会给人一种错误的印象，以为事情已经完成了，但事实并非如此。

## **忘记了什么？创建缓冲任务**

这是我最喜欢的一个，适合和完成任务。这是一个像缓冲器一样的任务，我通常会积累一些小的，但是需要做的事情，这些事情可能不适合一个或另一个代码审查的上下文。

评论中出现的任何评论可能与解决方案没有直接关系，但对编码风格的影响可能超过一个人正在工作的上下文，我总是会将其添加到 fit & finish 中。

这也可以用来包装东西，也许是做一些代码整理工作，或者添加你忘记的最后一个测试。

这是一个记录我们在开发过程中发现的所有小事情的好地方，并确保我们有时间解决它们。

软件工程是一个美丽的工作领域，因为一个人每天都在学习新的东西，但是如果我们超越技术方面，它也是一个惊人的领域来发现和调整:我如何处理不同的问题？我如何协作并让我的工作可见？今天，我们很少会遇到两个完全相同的任务，但是我们用来解决它们的原则仍然是相同的。随着时间的推移，我们成长并理解:在一个协作和敏捷的工作环境中，我如何最有效率？

这三年时间(2014-2017)是我在上述所有方面的学习过程，是塑造我今天这个工程师的重要部分，为此我很感激。我仍然每天都在学习、成长和发现。