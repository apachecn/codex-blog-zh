# 角度延迟加载

> 原文：<https://medium.com/codex/lazy-loading-in-angular-23d8c45dc811?source=collection_archive---------17----------------------->

构建软件不是一个简单的任务，开发人员必须做很多额外的工作，即使你的登录页面显示了登录按钮。

![](img/8ecbb0cf8c46a229ccaf34ca1a5bd502.png)

将代码打包成块

写代码来完成一项任务总是第一件事，但是如果你想构建一个好的软件，还有很多事情要做。维护、记录、扩展和文档化是使软件变得更好的几个步骤。

在这篇博客中，我们将讨论 angular 项目的缩放，在缩放中，我们将讨论一个非常具体的主题，即延迟加载。在前端方面，加载网站是最重要的事情，因为它的性能和开发者必须最关注它，但在某些情况下，当代码库增长时，开发者也无法避免前端构建的大捆绑。

我想到的最好的例子之一是电子商务。电子商务项目是最终增长的项目，你无法避免这一点，因为首先你必须开发与用户相关的一切，然后你必须开发与管理相关的一切，因为管理面板是不可避免的，你必须建立它，但这使你的应用程序比你计划的要大得多。当您为这个应用程序构建一个版本时，这个版本是如此之大，以至于要花很长时间才能在 web 浏览器中加载。在这里你可以注意到一件事，即使你的应用程序是由一个普通用户使用的，那么管理部分 Kodi 也被加载到 web 浏览器中，这使得它加载太慢。管理员也是一样，每当管理员使用应用程序时，用户部分的代码也会加载到浏览器中，这很烦人。

现在，为了避免这种情况，出现了延迟加载。因此，惰性加载的基本定义可以是，你只加载应用程序中与当时正在使用应用程序的用户相关的部分。这将避免不必要的加载，但会增加浏览器的加载时间。即使在同一个模块中，你也可以做一些延迟加载，比如说用户有两个不同的页面，所以你首先只加载登陆页面，然后延迟加载其他页面，这将帮助你快速加载网站。

angular 框架具有惰性加载整个模块的内置功能，因此您可以将整个项目划分为不同的模块，然后您可以根据需要加载这些模块。这有助于您更快地加载应用程序，并提高应用程序的性能。在一个有角度的框架中做到这一点非常简单。在我的 angular 13 教程的一个视频中，我解释了如何在 angular 应用程序中进行延迟加载，所以如果你真的想知道延迟加载在 angular 中是如何工作的，你可以查看视频，我会在博客中分享链接。

[链接](https://youtu.be/zugQ03owIfg)获取 Angular 13 中如何懒加载模块的视频教程。

祝大家开心！！！！！