---
title: 关于本指南
---

本指南分为几个部分，类似于课本。 每个部分都建立在前一部分的内容上，但是没有必要按顺序阅读指南。 [Key Topics](key_topics.md)页面旨在链接到能够理解架构和开始构建插件所必需的页面。

> **NOTE** 浏览本指南时，您会注意到有些主题显示为灰色。 不幸的是，该指南并不完整，并包含某些主题的占位符。 我们正在努力扩大覆盖范围，但是如果您由于缺少内容而陷入困境，请参阅[获得帮助](getting_help.md)部分以了解有关如何再次移动的详细信息。
>
> 这一份指南也在[GitHub](https://github.com/JetBrains/intellij-sdk-docs)开源了, 并总是感激地收到新内容的请求。 合并请求不需要全面综合 - 如果一个小小的更新可以帮助你，它也会帮助其他开发者！ 所有拉请求将被接受之前审查，所以不要担心不准确。 请参阅[贡献](/CONTRIBUTING.md) 页面 查看有关在本地建设指南和贡献的详细信息。
* [**Part I - 插件**](/basics.md)

    介绍如何创建一个可以扩展_IntelliJ Platform_的插件。 包括如何设置项目，注册扩展点，指定_IntelliJ Platform_的特定版本以及如何打包，部署和测试插件的详细信息。

* [**Part II - 结构**](/basics/architectural_overview.md)

    提供关于*IntelliJ Platform*体系结构的高层次介绍性概述，了解它是如何分解成几个层次的 - 基础平台，项目模型，功能等等。 它还介绍了程序结构索引（PSI），它为_IntelliJ Platform_提供了许多不同语言的语法和语义模型。

* [**Part III - 基础平台**](/platform/fundamentals.md)

    介绍该体系结构的基础层，它提供了许多功能和实用程序，如组件模型，用户界面，文档和编辑器，虚拟文件系统，设置和线程以及后台任务。 基本平台层本质上包含*IntelliJ Platform*的功能，该功能不针对语言功能或解析。

* [**Part IV - 项目模型**](/reference_guide/project_model.md)

    记录项目模型，它表示当前加载的项目的文件和配置，以及用于构建项目的构建系统。

* [**Part V - PSI**](/basics/indexing_and_psi_stubs.md)

    程序结构索引为许多不同的文件类型建立语法和语义模型。 本节介绍如何使用PSI，浏览和操作语法树，还要查看强大的引用系统，它允许语法树节点引用语义模型中的项目。 它还详细介绍了PSI如何创建和使用索引。

* **Part VI - 特征**

    介绍如何扩展和使用PSI图层的各种功能进行交互，如代码完成，导航，<kbd>Alt</kbd> + <kbd>Enter</kbd>项目，意图，重构等。 另请参阅下面的“自定义语言”部分，了解仅在添加对新语言的支持时适用的语言特定功能。

* [**Part VII -产品特定**](/products/idea.md)

    _IntelliJ Platform_中的许多功能都是语言和产品不可知的。 例如，代码检查在Java中的工作方式与在Ruby中的工作方式相同，只是语法树和语义信息不同。 本节介绍产品的特定功能，如特定的项目模型差异以及如何将其定位到插件中。

* [**Part VIII - 自定义语言**](/reference_guide/custom_language_support.md)

    插件经常扩展对现有语言的支持，例如添加对Java文件的检查。 本节介绍如何向_IntelliJ Platform_添加对默认不支持的新语言的支持，创建解析器，语法和语义模型以及构建在顶部的所有功能。

* **Part IX - 自定义IDE**

    介绍如何使用_IntelliJ Platform_创建新的自定义IDE，而不是插件到现有产品，例如 如WebStorm或Android Studio。

* [**Part X - 插件库API**](/plugin_repository/index.md)

    记录JetBrains维护并用于托管插件的[Plugin Repository](https://plugins.jetbrains.com)服务的API。 没有必要知道这个API来发布插件 - 插件可以手动上传，或通过Gradle IntelliJ插件。

* [**Appendix I - 教程**](/tutorials.md)

    提供工作示例代码的教程和链接，以演示与_IntelliJ Platform_相关的各种功能和功能。

* [**Appendix II - 资源**](/resources.md)

    链接到有用的资源，例如IntelliJ Community Edition源代码，Plugin Development论坛和Plugin Developers Gitter room。
