# 我的系统设计访谈和这本书的起源

> 原文：<https://medium.com/codex/my-system-design-interviews-and-the-genesis-of-this-book-80ae825099f7?source=collection_archive---------3----------------------->

## 文章

## 《系统设计访谈》的作者谭志勇

*在这篇文章中，谭志勇探索了他职业发展中导致成功的方面，并为他的书埋下了种子，这本书现在可以在曼宁早期访问计划中获得。*

*如果你想学习关于高级软件工程和系统设计面试的技巧、诀窍和经验，读读这篇文章。*

通过在[manning.com](https://www.manning.com/books/acing-the-system-design-interview?utm_source=medium&utm_medium=referral&utm_campaign=book_tan_acing_6_16_22)结账时将**FCT an**输入折扣代码框，在系统设计面试 中获得 25%的折扣。

当我 2013 年获得电气工程硕士学位时，我几乎不知道如何编码。我在单个文件中编写 20 多行代码的经历是编写 MATLAB 脚本来处理一些现场测量或绘制简单的 3D 图，或者是我作为研究生参加的大二课程的 C++作业，这是一种半被误导的“学习编码基础知识”的努力。我买了一本 Gayle Laakmann McDowell 的第五版《破解编码访谈》,接着学习 Java(泛型花了我一段时间才理解),在过去的一年里才刚刚学会基本的数据结构。

![](img/07d2d92834f92e858c494f27ba55719a.png)

我在一家初创公司找到了一份数据工程师的工作，这是一个没有受过正规计算机科学教育的人可以进入的入口，我愉快地完成了为机器学习编写 Python 脚本的工作。我的好奇心驱使我去面试软件工程师职位，这导致了我在 2014 年和 2015 年的第一次系统设计面试。我退出了我的第一次面试，因为我知道这不是编码面试。其中一次，我甚至把它当成了一次数据工程面试。我的面试官要求一个应用程序来访问某些数据。我在白板上画了数据库模式，并解释了一个 ETL(数据)管道来获取他想要的数据。我的采访者评论说，他从未见过有人像我这样处理这个问题。显然，这是他第一次面试数据工程师。我没有得到一个提议。我也很难进一步了解这些系统设计面试。当时，我在一个只有几个工程师的小办公室里，讨论面试不是一个明智的想法。

2015 年，当我走进一家知名科技公司的系统设计面试时，我不知道这将是我这一年中最重要的事件。我用我通常画表格和管道的方式回答了面试官的问题，他指示我画方框来代表服务或数据中心，用它们之间的箭头来代表它们的通信。在接下来的 50 分钟里，我们讨论了数据中心之间的复制(复制数据)，因此，智能手机或笔记本电脑上的用户可以从同一国家的数据中心加载数据，而不是从另一个洲的数据中心加载，这样会快得多。他问我这是否会导致数据不一致(不同数据中心上的数据不同)，关于在一个数据中心停机的情况下将流量重新路由到其他数据中心以保持服务可用性，并向我介绍了许多其他基本的系统设计面试概念。回想起来，我相信我的面试官从我的简历和我们在一起的最初几分钟就知道我没有准备好担任软件工程师的角色，他决定利用这一小时向我介绍系统设计面试。

和一个好工程师在一起的那一个小时是改变一生的事件。有时候，我们需要的只是被指向正确的方向。我开始阅读关于可伸缩性的书籍，研究关于各种示例系统设计问题的在线文章和视频，比如设计 Craigslist 或 Flickr。随着继续练习编码面试，这帮助我通过了 2016 年优步大学的软件工程师面试，在接下来的 4 年里，我在那里获得了长足的发展。

当我在 2020 年初再次开始面试时，我注意到有更多的在线资源可用。网上内容的总量、主题的多样性和质量的变化给我留下了深刻的印象。我搜了系统设计面试的书，没找到好的。然而，我确实找到并研究了一些关于可伸缩性的好书。在一个这样的下午，我一边做笔记和截图，一边看完了另一个系统设计面试视频。我浏览了一下笔记，然后停下来看了一会儿屏幕，思考着我的学习之旅。想起了 2015 年那次面试。我记得自己当时和其他时候，在我生命中的多个时期，我比必要的时间更长，更努力地工作，因为我在我的软件工程职业生涯中走了一条非正统的道路，缺乏正规的教育和导师，我后来学会了欣赏他们的价值。我想起了我的努力，我的天真，还有那个指导我的面试官。我想到了其他走在同一条路上的人。如果没有适合他们的好书，那我就用我的笔记写一本。这一刻成了我这本书的种子。

> 他们可能知道你会用你的忠告来引导我。
> 
> *——诗篇 73:24*

## **什么是系统设计面试？**

系统设计面试是两个工程师之间的对话。给定一些模糊的需求，这些工程师将讨论和定义更明确的需求，然后是工程团队可以实现的工程设计。有许多问题和考虑。我们如何将这个系统划分为组件，在系统开发的哪个阶段将一个组件分离为一个独立的服务是有意义的？我们如何将某些所需的复杂性分离成对许多不同系统有用的组件？哪些组件比其他组件需要更多的硬件资源，我们如何通过将特定的硬件分配给最需要的组件来最大限度地提高性能和降低成本？在设计和实现一个给定的系统时，需要考虑哪些潜在的人为因素？我们可能会遇到哪些其他问题和限制？

![](img/bd0c36e74db13866d83e2d4632200839.png)

这个讨论是开放式的，但是我们可以在系统设计访谈中识别模式。这有助于我们在面试的 50 分钟内最好地展示我们的能力。一个常见的主题是设计一个可伸缩的 web 服务，让用户可以通过互联网进行交互，这种服务可以快速、经济地伸缩，为几个用户到几十亿用户提供服务。

## **为什么要进行系统设计？**

为什么系统设计如此重要和相关？我们必须确保我们正在构建的系统能够很好地为用户服务，并有效地帮助他们实现目标。我们的系统还包含用于公司目的的功能，其中可能包括创收功能，如计费、分析功能，这些功能可以让我们了解用户接受情况，并让我们了解未来可能的发展方向，等等。构建一个系统及其特性需要大量的代码、时间和精力。作为软件工程师，我们每天都在编码，我们每天的代码输出必须尽可能高效地让我们更接近目标。要做到这一点，我们必须详细了解我们正在构建的系统，这样我们就知道我们可以使用哪些平台和其他系统，我们需要自己编写系统的哪些部分，以及如何将它们放在一起。

更进一步，作为一名初级工程师，你可能详细了解你的系统，但看不到组成你公司的许多其他系统。另一方面，首席技术官或架构师做出广泛的决策，消耗了公司的大量稀缺资源。随着你资历的提升，你很快就会达到一个点，你没有时间去了解所有的细节。您公司开发的平台可能有五万个类，成百上千的工程师在您公司的各种系统上工作，更改代码的速度比您阅读代码的速度快得多，并且至少几十个小组会议可能同时进行，以讨论新的或当前的项目。为了做出可能对整个组织甚至全世界产生深远影响的最佳决策，您必须了解公司各种系统的高级细节，并提出正确的问题。这将帮助你知道你的注意力和你的组织的努力集中在哪里，你能负担得起在哪里分配实验资源，以及何时何地你必须改变路线并减少损失。

系统设计面试是涉及这些因素的讨论或角色扮演。类似于现实生活，你将有有限的时间去理解和讨论这个系统。面试讨论将不超过 50 分钟，太短了，无法讨论复杂业务逻辑的错综复杂的细节。你必须保持高水平的讨论，将问题分解成元素，并通过流利地放大任何特定元素并讨论其细节的能力来展示你的技术深度。类似于一个工程领导，你可能不知道所有的细节，比如算法。但是，您确实知道如何提出正确的问题，以确保贵公司的工程资源得到最佳分配，系统能够经济高效地满足您的用户要求和我们公司的利益，系统的开发方式能够预测未来可能的要求，预测我们的应用程序开发可能采取的方向，并考虑未来可能的限制，如资源限制或法律和隐私要求。您可以将设计系统的各种方法概念化，讨论它们的权衡，并预测任何特定方法可能出现的问题。

系统设计讨论也是团队协作中的常见练习，是工程师日常生活的一部分。为团队的系统设计讨论出谋划策是团队中每个工程师的职业职责。讨论可以通过各种渠道进行，如 RFC 等工程文档的评审和评论、聊天室或会议。会议非常类似于系统设计面试。这些会议可能是为了讨论要开发的新系统，当前系统中问题的解决方案，或者产品或工程经理要求的新特性。这些会议可能或长或短，但都是有限的，工程师必须面对的一个常见情况是在不知道所有细节的情况下询问相关问题，提出相关的关注点和想法。系统设计面试也可能是一个练习，讨论集团或公司的愿景以及基于当前情况的可能方向。

![](img/6eca70d9ce866a63539b58e2d9b96764.png)

## **系统设计和你的权力**

由于 web 服务完全由运行在广泛可用的数据中心上的软件组成，因此它们不需要任何长时间的准备工作，并且可以在很短的时间内开发，根据系统的复杂性和公司的资源，开发时间从几天到几个月不等。有了良好的产品市场匹配，就可以吸引相当一部分的世界人口使用一种产品。一家能够很好地执行产品路线图的科技公司可以获得巨大的经济(甚至政治)实力。在过去十年中，科技公司在市值最高的公司名单中所占比例过高，即使最近科技股在 2022 年年中出现低迷，这 10 家公司中至少有 6 家仍然是科技公司。Alphabet、亚马逊、苹果、字节跳动、华为、Meta、腾讯、优步等知名科技公司直接影响着数十亿人的生活，因此经常受到媒体、政治家和政府官员的关注。一家拥有优秀工程师的科技公司，如果能够设计和实现具有可伸缩、可维护和易于扩展的架构的优秀系统，将会在很多年内保持领先地位。

经济回报可能会很高。无论规模大小，高级软件工程师在大多数组织中的薪酬都很高，公共部门和私营行业对他们的需求都很高。仅此一点，就是很多人努力成为大公司高级软件工程师的强大动力。至少，学习系统设计会提高你在一个有好工作和无尽应用的行业中的地位。

就像那位采访者让我看到了一个新的世界一样，我希望这本书可以为那些阅读它的人打开一个充满机会的新世界。如果知识就是力量，那么给予知识就是给予力量。如何运用你的新能力取决于你自己。即使你加入了一家大公司，在那里你可能会觉得自己是一个无足轻重的小人物，但最好记住你仍然有权力。精通系统设计让你有能力领导工程团队设计和实现影响更多人的系统，这些人比你想象的要多。您可以使用新获得的系统设计专业知识来设计系统，为小型企业或众筹慈善事业提供支付处理。你可以通过允许艺术家和企业家在没有大型媒体公司或政府许可的情况下接触到更多的观众，来使社交媒体公司的创造力和企业家精神民主化。或者，你可能会选择为无数应用中的任何一个开发软件，比如高速列车、自动驾驶汽车、石油和天然气钻井平台，或者华尔街的高频交易系统。对有能力的软件工程师的需求和可能性是无止境的。

我希望你在你的系统设计学习经历中，以及在你用你的新能力做什么的选择中，一切顺利。

如果你有兴趣了解更多，你可以在这里找到我的书。