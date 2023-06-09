# 一起更好:ReacType、路由器和上下文 API

> 原文：<https://medium.com/codex/better-together-reactype-router-and-context-api-6408435f0d81?source=collection_archive---------9----------------------->

![](img/bdd8762603a302c9e9dbf54c9310a932.png)

塔玛斯·帕普拍摄的照片

# ReacType 是什么？

根据技术加速器[操作系统实验室](https://opensourcelabs.io/)的使命，ReacType 是一个桌面应用程序，它通过提供一个强大、可扩展和高效的原型工具来增强开源开发者社区，该工具有利于所有经验水平的开发者的工作流。ReacType 拥有快速的拖放原型界面，将实时预览与闪电般快速的导出功能相结合，抽象出启动新项目所需的耗时的锅炉板，将更多时间留给困难的开发人员决策和挑战。使用 ReacType，开发人员只需 20 分钟，就可以使用完全配置的 Webpack、Express backend、Enzyme 和 Jest 测试套件构建并导出一个功能完整的 React 应用程序，而无需编写任何代码。

本文将深入探讨 ReacType 9.0 团队添加的特性。对于已经存在的功能和特性的概述，请随意查看[更智能地工作，而不是更难地创建一个具有 React type](/front-end-weekly/work-smarter-not-harder-to-create-a-react-app-with-reactype-94dd60be5873)和[React type 8.0 的 React 应用程序:您首选的 React 原型工具现在导出测试](/@wbrittwage/reactype-8-0-your-preferred-react-prototyping-tool-now-exports-with-tests-7ae5b1666fd2)。

# 9.0 有什么新特性？

用户现在可以利用 **React 路由器**和**全局状态管理**以上下文 API 的形式用于他们的应用。

# 为什么选择 React 路由器？

尽管 ReacType 总是能够处理多个可重用的 React 组件，但用户无法在一个应用程序中链接和路由这些组件。这种功能的缺乏使得 ReacType 无法真实地原型化能够从动态路由中获益的单页面应用程序。为了解决这个问题，我们选择实现 React Router，因为它能够动态执行客户端路由，允许在组件和页面之间导航，而无需刷新整个页面，从而带来更加无缝的用户体验。

# 它是如何工作的？

在拖放菜单中，现在有一个新的 React Router 部分，它有两个可拖动的 React Router 元素:LinkTo 和 Switch。

LinkTo 作为 React 路由器链路运行。只需将一个 LinkTo 拖到画布上，导航到 Customization 菜单，然后将文本字段更新为链接将显示的内容(即“Home”)和到一个端点的链接(即“/home”)，该端点将对应于我们稍后将添加的路线。一旦我们在自定义菜单中点击保存，我们将看到链接出现在演示渲染面板上。作为 ReacType 9.0 的一个新增特性，端点现在将在 Link 和 LinkTo 元素上显示为蓝色，以帮助我们直观地跟踪应用程序中的所有路由。

一旦我们将一组 React 路由器链接添加到画布中，我们现在就可以将它们路由到 React 路由器交换机中的可重用组件。作为补充，React Router Switch 元素的操作类似于 Javascript switch 语句，并允许我们的应用程序以独占和声明的方式呈现路由。

首先，将一个交换机拖到我们的画布上，然后单击出现在交换机上的+按钮来添加路由，这将自动嵌套到我们的交换机中。每条路由都需要被定向到一个与 LinkTo 端点相对应的端点，因此我们可以通过导航到路由的定制菜单并使用 Link 字段添加相应的端点来添加它。与 LinkTo 端点类似，路由端点将出现在画布中，以增强开发人员的体验。最后，通过将一个可重用的组件拖到适当的路径中来完成路由。在 ReacType 9.0 中，被拖到画布上的可重用组件将保持精简，以减少混乱并增加画布上的可读性。现在，我们将重复这个过程，直到我们为 LinkTo 元素找到匹配的路由元素。

这就是全部了！我们可以通过单击画布右侧的实时更新演示渲染面板中的链接来确认 React 路由器链接和路由正在工作，并且我们可以导航到代码预览菜单来验证 ReacType 会自动将 React 路由器以及相应的语法和标记导入到我们导出的代码中。

# 为什么是全局状态管理？

我们对 ReacType 做的第二个关键添加是添加了全局状态管理。React 的关键构建块之一是组件对其他组件的变化做出响应，作为 React 开发人员，我们跟踪这些变化，并通过利用状态对它们做出响应。虽然在较小应用程序中，利用本地状态管理和适当的钻取来利用状态肯定是可能的(有时甚至是更可取的)，但是这种形式的状态管理对于较大的应用程序来说远非理想，因为它会增加代码的膨胀，同时降低可读性和可维护性。

考虑到这一点，ReacType 9.0 团队的目标是为 ReacType 提供首个全球状态管理解决方案。

# 我们是如何使用上下文 API 的？

最流行的 React 全局状态管理解决方案是 Redux、反冲. js 和上下文 API。虽然这三个选项都可以完成这项工作，但 ReacType 9.0 团队希望选择一个选项，为使用该工具的开发人员增加最大的效用和好处。

Redux 非常强大，并拥有广泛的使用和支持基础，但对于企业级应用程序来说，它往往是更好的解决方案，因此对于一般 ReacType 用户构建的应用程序规模来说，Redux 不是合理的选择。另一方面，反冲. js 将非常适合 Reactype 用户倾向于构建的应用程序的规模，但是反冲. js 仍然被认为是一个实验性的状态管理库，还没有被广泛采用，我们希望我们的状态管理解决方案能够让尽可能多的开发人员受益。

这就给我们留下了 Context API，它是一种组件结构，作为它的轻量级全局状态管理解决方案来对钻柱进行反应。作为一个额外的好处，上下文 API 与功能性 React 组件配合得非常好，这是 ReacType 已经在使用的，所以我们的团队决定继续实现它。

# 它是如何工作的？

首先，我们需要给我们的应用程序添加一个有状态的值。只需选择一个组件，使用创建面板添加一个键-值对，并键入要添加到应用程序状态中的内容。一旦我们添加了一个有状态值，我们可以在代码预览中看到相应的上下文语法和钩子将包含在我们导出的代码中。

为了使用我们的有状态值，我们将首先在一个组件中选择一个 HTML 元素，然后导航到 Customization 菜单。在这里，我们将单击我们希望在其中使用状态的输入字段旁边的“使用状态”按钮，以弹出“选择状态源”菜单。该菜单显示了应用程序中每个组件的状态。

从 ReacType 9.0 开始，state 可以作为嵌套的复合数据类型添加，因此如果是这种情况，那么该菜单将递归地进入复合数据类型，直到到达原始数据类型，此时选择将返回到相应的数据字段。

当我们做出选择后，我们可以点击保存，并看到我们的选择渲染到演示渲染屏幕。最后但同样重要的是，我们可以在代码预览中看到，我们已经将实际变量传递到 HTML 元素中，该变量对应于我们刚刚在选择状态源菜单中单击的值。

# 介入

您可以在我们的 [**Github**](https://github.com/open-source-labs/ReacType) 上找到 ReacType，或者访问我们的 [**网站**](https://reactype.io/) ，在那里您将遇到启动和运行它所需的一切。贡献者一直在寻找改进 ReacType 的方法，所以我们希望听到您的意见！欢迎在 Github 上提交任何问题或贡献自己的力量。

在下面的链接中关注 ReacType 9.0 的成员:

**克里斯唐↪** [**领英**](https://www.linkedin.com/in/chrisjtang/)**/**[**github**](https://github.com/chrisjtang)

**crys lim↪**[**LinkedIn**](https://linkedin.com/in/crystallim)**/**[**github**](https://github.com/crlim)

**荣富↪** [**领英**](https://www.linkedin.com/in/ronfu)**/**[**github**](https://github.com/rfvisuals)

**威廉·程↪** [**领英**](https://www.linkedin.com/in/william-cheng-0723/)**/**[**github**](https://github.com/WilliamCheng12345)