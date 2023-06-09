# 您的工程总监不希望您优化利用率

> 原文：<https://medium.com/codex/your-engineering-director-does-not-want-you-to-optimize-for-utilization-a48ad0368b8?source=collection_archive---------5----------------------->

## 挑战你的基线假设，这样你就可以有意识地优化结果。

我注意到，当留给他们自己的设备时，人们倾向于优化利用率。

![](img/420cd7eb694c722bf38f4a8f18c73df9.png)

布雷特·乔丹的照片

# 优化利用率让人感觉效率很高。

这是它的样子。你正在做一项任务，不知何故遇到了一个障碍，需要一些时间来解决——比如说半天。所以，当有人为你清除了路障，你就开始了另一项不同的任务。

从表面上看，这似乎不是一个问题。毕竟，你不想浪费时间，而且你正在推进工作。有几种方法可以解决这个问题。

> *无论你采取什么方法，挑战你的基线假设，这样你就可以有意识地为正确的事情进行优化。*

一种方式是你的第二个任务需要很长时间才能完成。假设两天。因此，即使在第一个任务被解除阻塞后，您可以继续执行它，但在您完成第二个任务时，它将处于闲置状态。

另一种选择是停止任务二，回到任务一并完成它，然后再回到任务二。这有利于完成任务一，但是任务二将花费比预期更长的时间。

有时，您可能会在任务一和任务二之间来回切换，从而增加两个任务的运行时间。这两个任务越不相关，每次你**切换环境**的时候，你就会产生越多的开销。

> 一天中切换上下文超过 2 到 3 次可能会耗尽你一天的大部分生产力！

这种转换失败的另一种方式是任务二也可能被阻塞。所以现在你有两个任务，在继续前进之前，你在等待一些外界的解决方案。像任何通情达理的人一样，你不想浪费时间，所以你选择了第三项任务。

现在我们刚刚描述的问题都被放大了。你每增加一项任务，问题就会成倍增加。每一项不同的任务都会增加更多的时间！

如果你在一个团队中工作，一个额外的问题悄然而至。你可以排干积压的工作。现在，当一个团队成员在寻找他们的下一个任务时，没有什么可做的。你的队友无事可做，而你却在应付三项任务(却一项也没完成。)

这就是你优化效率的结果！你的队友在挨饿，你在狼吞虎咽，却一事无成。相当高效！？！？！

大多数人不知道，或者不承认他们是为了效率而优化。感觉你是一个尽职尽责的团队成员。意图是积极的。不过，这些假设可能是隐藏的。问问你自己和你的团队，“我们在优化什么？”

# 我们还能优化什么？

让我们来看一个不同的模型。

让我们重新开始，在这里，你拿起任务一，它变得受阻。除了接另一个任务，你还能做什么呢？我想到了几个选择。

你可以让你的队友知道你有空，并请求帮助完成任何已经开始的任务。这可能包括与队友配对，执行代码审查，进行设计审查，以及测试应用程序。也可能是把某人的任务中可以独立完成的部分切掉。

这些方法都有助于加快现有工作的速度，而无需开始任何新的工作。这是限制“进行中的工作”的精益概念但是限制听起来不像你在优化什么。这是怎么回事？

> 挑战你的基线假设，这样你就可以有意识地为正确的事情进行优化。

您正在限制正在进行的工作，以最大限度地提高现有任务的完成速度。我们对一个指标进行了限制，这样我们就可以影响另一个指标。我们正在优化吞吐量，即任务开始后完成的速度。

吞吐量是对运行时间的度量。所以这不是你在一项任务中投入的时间。它是一项工作从开始到结束的总时间。如果你在四周内每周花一天完成一项任务，你会看到一个有趣的结果。您的工作是四天，但是经过的时间是原来的 7 倍——4 周！这个任务的**周期时间**是 28 天！

如果你能直接完成这个任务，它肯定不需要四天，因为环境切换会更少。不要被骗以为没有成本。

软件开发领域的上下文切换成本大约是 15-30 分钟。你切换的不同领域越多，成本就越高。您启动的环境越复杂，成本就越高。

在一个普通的工作日中，一天中切换上下文超过 2 到 3 次可能会抹杀当天的所有生产力！

现在我们有了第二种方法，我们正在优化以减少周期时间和增加产量。对于一个专注于交付和完成的团队来说——对于一个专注于成就的团队来说——*这个*应该是优化的默认模型。

第一种方法将开发人员置于模型的中心。我们正在优化以充分利用开发者。毕竟我们为开发者付出了很多，所以要优化让他们忙起来。你看到了吗？忙碌(利用)变得比有效(完成任务)更重要！)

> *这就是优化效率的结果！你的队友在挨饿，你在狼吞虎咽，却一事无成。*

第二种方法将工作放在模型的中心。我们需要采取一种不同的心态来支付我们的开发人员。我们付钱给他们是为了帮助他们完成工作。我们正在为工作的效率和流程投入稳定的资金。听起来更高尚，不是吗？

我们还能优化什么？让我告诉你我最近的一次谈话，让我们看看是否能提取出正在发生的事情。

# 谷歌优化了什么？

巴迪(*不是他的真名)*最近加入谷歌，成为 SRE 一个团队的经理。巴迪是一个有才华、有动力的人。他拥有计算机科学博士学位。他喜欢把事情做完。他被自己和团队的成就所驱使。

Buddy 对我发表了一个关于在 Google 工作的评论。“在谷歌的生活很奇怪…必须呆在我的车道上。”这激起了我的好奇心，所以我们约了些时间出去聊天。

Buddy 描述了一种环境，在这种环境中，工程师通常会同时进行几个项目。这些项目有方向，但没有明确的目标，也没有截止日期或时间表。经理是来帮忙的，是仆人式的领导者。他们不是来指导、指挥、评判或管理的。

这种模式违背了巴迪追求成就的初衷。在这种模式下，他*如何帮助*他的团队完成工作？

此外，管理层用 okr 来指导团队和组织，但是这些经常在过程中改变。高级管理层也有一个威利·旺卡风格的“金门票”概念。这使得他们能够迅速介入并“加速”特定项目的优先级。

Buddy 还描述了一个似乎与工程师的福利和关怀相协调的环境。谷歌在校园内提供许多服务和便利设施，包括所有膳食、洗衣、按摩、财务规划、健身、福利、按摩和冥想。这听起来像是一个旨在让你摆脱许多烦恼的环境，这样你就可以专注于工作。

我们陷入了关于“工作”的谈话。谷歌优化是为了什么？

这与利用率无关，因为尽管每个人都有多个项目，但是这些项目并没有被“管理”,也没有朝着集体成就的方向发展。这也与吞吐量无关，因为每个人都有多个项目同时运行。

我会把它描述为创造力和创新的结合。谷歌正在提供空间和环境，以便有才华的工程师能够发挥他们的最佳水平。他们减轻了很多照顾自己的压力。他们还积极消除外部力量的压力，如市场、客户、利益相关者和人为的最后期限。

# 什么是正确的方法？

我们的默认行为是优化感知效率。我们通过超负荷利用自己来做到这一点。这导致回报缓慢。

另一种方法优化正在完成的工作。限制正在进行的工作可以增加流量。结果就是源源不断的工作。

谷歌优化了开发者体验。他们建立了一个环境，最大限度地增加创造和创新的机会。

> 问问你自己和你的团队，“我们在优化什么？”

无论你采取什么方法，挑战你的基线假设，这样你就可以有意识地为正确的事情进行优化。

*👏🏻给我鼓掌* ***跟着*** *如果你喜欢这篇文章。*

## 📋关于米洛

我是一名科技高管、作家、演说家、企业家和发明家。我从 1995 年开始开发软件，过去十年一直在开发团队。🚀

我写关于软件、工程、管理和领导力的文章。

*你也可以* [*在 Twitter 上关注我*](https://twitter.com/milotodorovich) *。🐦*