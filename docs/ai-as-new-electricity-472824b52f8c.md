# AI 作为新电？

> 原文：<https://medium.com/codex/ai-as-new-electricity-472824b52f8c?source=collection_archive---------15----------------------->

![](img/242e5fe870be5b1f894e9c5cc614b2e3.png)

直到 2020 年 4 月:GPT 2 号是人工智能之王，拥有令人惊叹的 1.5 亿参数。

处理这件事并不容易。它需要 6GB 的磁盘空间，但这不是问题所在。问题在于处理速度:您必须等待几分钟才能在 CPU 上运行一个推理。如果你有至少 24 GB 显存的 NVidia GPU，那么使用 GPU 至少会快十倍。

不知何故，你开始希望微调它的行为。对于只有 124 M 参数的最小型版本来说并不难。拥有 8 GB 显存的 NVidia GPU，你能够在合理的时间内完成这项工作(以小时计),并通过使用莎士比亚的作品、圣诞歌曲等对其进行微调来体验这一点。你所需要知道的是如何准备输入来训练一个模型，这个模型将产生你想要看到的东西，这需要经验，但这不是火箭科学。

如果你想微调最大和最好的 GPT-2 …那么，在这种情况下，你会做同样的工作，但最多 2-3 周。速度变慢是因为你必须在 CPU 上完成所有的处理。如果之前用运行在 GPU 上的最小的 GPT-2 练习过，那么值得等待。

与此同时，有很多人工智能服务的云产品。亚马逊、微软和谷歌都有，其他小公司也有。使用云托管人工智能服务的优势:

1.  你不必关心基础设施(好吧，这是显而易见的)
2.  你不必知道你正在做的事情的所有细节。漂亮、吸引人、方便的用户界面允许你声明你想做什么，瞧，你有了。

但是，这里最重要的部分是，有足够的人力，你可以在本地计算机上做任何事情。好吧，如果你把语言翻译云引擎考虑进去的话，并不是所有的东西。谷歌和微软在这方面仍然表现出色，无论你在本地机器上做什么，都有无与伦比的质量。你猜怎么着:有些基于云的服务甚至让谷歌和微软成为语言翻译游戏的初学者。 [DeepL Translate:比如世界上最精准的翻译器](https://www.deepl.com/translator)。我尝试过，曾经是，现在仍然很着迷。

2020 年 4 月，对于每个亲身经历过的人来说，一个激动人心、令人震惊的惊喜降临了:GPT 3 号。凭借其 175B 参数，它超越了我们以前见过的一切。新手，告诉他你想让他做什么，他就会去做。不总是完美的，但足以让每个人哑口无言。然后出现了一些其他的模式，然后出现了中国的武道 2.0。中国的 GPT-3。只有更好:-)。

每个人都开始用“好的，这太棒了”，“AGI 方向要走的路”和其他(错过的)信息来看这些模型。那些巨大的语言模型不知道他们在说什么。他们所做的只是根据他们接受训练的文本语料库，产生最可能的文本作为给定文本的扩展。没有什么智能，只是非常计算昂贵的统计。

但这不是本文的重点。本文的重点隐藏在两个幕后的事实中，这两个事实是显而易见的，但却被高度低估了:

1.  模型没有打开。我们不知道是什么架构让实现它们的神经网络如此神奇。
2.  这些模型是如此之大，以至于只有少数公司能够负担得起托管和使用它们。
3.  有多少公司可以玩类似的工具，并试图成为一个竞争对手？

GPT-2 和 GPT-3 的发明者 OpenAI 与微软建立了联系，并独家授权给他使用。现在，他们都在寻找在这样一个巨大的语言模型上赚钱的方法。他们通过 web 服务公开其功能，这并不坏，因为这是向其他人提供它的唯一可能的方式。这里的关键词是“唯一可能的方法”。仅仅是因为你不能独自托管它，即使你可以访问所有你需要的文件。

因此，如果你甚至想出了如何在一些商业案例中使用它，你可以只访问你可以访问的但是由其他大公司托管的实例，例如微软或谷歌。而这样的公司，世界上并不太多。

从这个角度来看，在可预见的未来，事情会变得更糟。忘记托管一些足够聪明的人工智能模型。未来 AGI 路由的人工智能模型将比这大得多，这是肯定的。

由于上面写的:你想用人工智能？好吧，只要选择一个提供商并使用其服务。这就好比当你需要一个计算器来计算 3 位数的乘法运算时，你不得不去询问你所连接的大型计算机。你需要从 Excel 中获取？然后，Excell 将自动询问该机器。

这朝着用电的方向发展:每个人都需要电，每个人都使用电。尽管如此，没有人在内部生产:他们把设备插入电线，然后就能得到供应。

结果:我们将依赖其他人提供的人工智能。现在，我们能相信它吗？我们会知道模型是如何训练的吗？

结果:我们将来使用的人工智能应该由政府来管理。同样，现在电力也受到了监管:电力的哪些属性必须是可用的，并得到其他人的信任，这一点很清楚。在这里，其他人，我指的是每个需要“有常识能力的人工智能”的人。“常识性人工智能”是未来的人工智能。