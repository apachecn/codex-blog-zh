# Azure DevOps 管道优化

> 原文：<https://medium.com/codex/azure-devops-pipeline-refinement-c66f1ec60272?source=collection_archive---------1----------------------->

## 使用模板和条件改进基于 yaml 的管道

在我看来，基于 Yaml 的 Azure DevOps 管道是实现 CICD 管道的一个非常好的方式。使用模板和条件使它们更棒。为了让您能够使用这些特性，我将通过一个简单的例子向您展示这两个特性。

![](img/81feba3e310a0b8333037cae95038a08.png)

[KOBU 机构](https://unsplash.com/@kobuagency?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 出发点

在我们见证这两个特性的优势之前，我将向您展示一个标准的 YAML 文件，感受一下它是如何改进的。作为技术基础，我将使用我的另一个故事中的基于[回购的方法来处理 CICD 数据。](http://Databricks CICD using Repo approach using Azure DevOps | by Stefan Graf | CodeX | Jul, 2022 | Medium)

那么，这个管道有什么问题。公平地说，只要我们只针对一个环境，并且只有一个分支触发我们的管道，就没有分支。*(注意:一个明显的问题是我们的秘密集成没有密钥库或类似的东西，但出于简化的原因，这被搁置了)*但如果我们想将这个解决方案应用到现实世界中，我们应该对它进行一些改进。

想一想，当我们将部署到各种环境中时，什么将很快成为一个问题？会有很多复制粘贴的样板代码。基本上，我们只需要为 3 个不同的环境复制我们的 Bash 任务 3 次。这可以通过使用**模板**来解决。

当我们有不同的分支作为触发事件时，会有什么问题呢？好吧，如果你处理每个分支都一样，那就没有了，但是如果你想不同地处理你的分支，你要么必须为每个触发器创建不同的文件，要么你可以使用**条件。**

## 模板

假设我们想要部署到 3 个不同的环境(TST、INT、PRD)。我们当然不希望相同的代码用不同的变量重复三次。我们应该用模板来代替！

模板是一个非常棒的特性。你只需要再创造一个。yml 文件，并可以在父管道中引用它。最佳实践是将模板保存在/templates 文件夹下，以保持整洁。让我们看看我们用例的模板是什么样子的:

这看起来与普通的 yml 管道非常相似！注意，我们不需要定义触发器和池。参数是我们将变量输入管道的方式，由$ { { parameters }使用。name}}。除此之外，它只是一个普通的管道，将我们之前的逻辑包装成可重用的格式。

现在，我们可以将该模板集成到父管道中，如下所示:

我们唯一需要做的就是使用-template 特性。在那里，您可以使用从父管道到模板管道的相对路径。此外，您可以为每个环境交付您的变量。这通常是通过为每个环境使用变量组来完成的。

## 情况

条件是让你的管道更加灵活的好方法。您可以使用众所周知的 if-else 逻辑来检查管道提供的几乎每个变量。在我们的例子中，我们将检查分支，这触发了我们的管道来决定我们是要部署到 TST(由主分支触发)还是 INT 和 PRD(由发布分支触发)。

此功能的使用方式如下:

if-else 逻辑的实现方式如下:

```
- ${{ if contains(variables[‘Build.SourceBranch’], ‘releases’) }}- ${{ else }}:
```

基本上，这将检查触发管道的分支是否包含单词 releases。如果是这样，它就调用相应的模板，如果不是这样，就执行 else 逻辑。

# 结论

Azure DevOps 为您提供了实现生产级 CICD 管道的能力。这是由一个广泛的工具集完成的，包括但不限于我在这篇博客中展示的这两个很酷的特性。希望你能学到新的东西！