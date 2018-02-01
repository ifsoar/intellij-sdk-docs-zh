---
title:什么是 IntelliJ Platform？
---

_IntelliJ平台_本身并不是一个产品，而是为构建IDE提供了一个平台。 它被用来驱动JetBrains产品，如[IntelliJ IDEA](https://www.jetbrains.com/idea/), [WebStorm](https://www.jetbrains.com/webstorm/), [RubyMine](https://www.jetbrains.com/ruby/), [DataGrip](https://www.jetbrains.com/datagrip/) and [Rider](https://www.jetbrains.com/rider/). 它也是开源的，可以被第三方用来构建IDE，比如google的[Android Studio](https://developer.android.com/studio/index.html) .

*IntelliJ Platform*提供了这些IDE需要提供丰富的语言工具支持的所有基础设施。 它提供了一个组件驱动的，跨平台的基于JVM的应用程序主机，具有高级用户界面工具包，用于创建工具窗口，树视图和列表（支持快速搜索）以及弹出菜单和对话框。

它还包括图像编辑器和全文本编辑器，并提供语法高亮，代码折叠，代码完成和其他丰富文本编辑功能的抽象实现。

此外，它还包括可插入的API以构建常见的IDE功能，如项目模型和构建系统。它还提供了非常丰富的调试体验的基础设施，具有语言不可知的高级断点支持，调用堆栈，监视窗口和表达式评估。

但是_IntelliJ平台的真正实力来自于计划结构指数（PSI）。这是一组功能，可用于解析文件，构建丰富的代码语法和语义模型，并从这些数据构建索引。这提供了许多功能，从快速导航到文件，类型和符号，到代码完成窗口的内容，并找到用法，代码检查和代码重写，快速修复或重构，以及许多其他功能。

*IntelliJ Platform*包含许多语言的解析器和PSI模型，其可组合性意味着可以添加对其他语言的支持。

## 插件

构建在*IntelliJ Platform*上的产品是可组合的应用程序，该平台负责创建组件，并将依赖注入到类中。 *IntelliJ Platform*完全支持插件，而JetBrains则拥有一个[插件库](https://plugins.jetbrains.com) 可以用来分发支持一个或多个产品的插件。 也可以托管你自己的仓库，并分别分发插件。

插件可以通过多种方式扩展平台，从添加简单的菜单项到添加对完整语言的支持，构建系统和调试器。 *IntelliJ Platform*中的许多现有功能都是作为插件编写的，可以根据最终产品的需求包含或排除。 请参阅[插件]一节(/basics.md) 获取更多细节.

*IntelliJ Platform*是一个JVM应用程序，主要用Java和Kotlin编写。 您应该熟悉这些语言和相关的工具，才能为基于*IntelliJ Platform*的产品编写插件。 目前，无法在非JVM语言中扩展*IntelliJ Platform*。
## Open Source

*IntelliJ Platform*是开源的，在[Apache许可证](https://github.com/JetBrains/intellij-community/blob/master/LICENSE.txt) 和 [在GitHub上托管](https://github.com/JetBrains/intellij-community)之下.

虽然本指南将*IntelliJ Platform*作为单独的实体引用，但没有“IntelliJ Platform”GitHub仓库。 相反，该平台被认为是与IntelliJ IDEA社区版几乎完全重叠，IntelliJ IDEA社区版是IntelliJ IDEA Ultimate的免费和开源版本(上面链接的GitHub仓库是[JetBrains / intellij社区](https://github.com/JetBrains/intellij-community) 仓库).

IntelliJ IDEA Ultimate是IntelliJ IDEA Community Edition的超集。 它基于社区版，但包括封闭的源代码插件（[请参阅此功能比较](https://www.jetbrains.com/idea/features/editions_comparison_matrix.html)). 同样，WebStorm和DataGrip等其他产品都基于IntelliJ IDEA社区版，但是包含了一组不同的插件，不包括其他默认插件。

这允许插件将多个产品作为目标，因为每个产品都将包含基本功能以及IntelliJ IDEA Community Edition回购的一些插件。 这就是我们所说的*IntelliJ Platform*。

通常，基于*IntelliJ Platform*的IDE将包含`intellij-community`仓库作为Git子模块，并提供配置以描述来自`intellij-community`的哪些插件，以及哪些自定义插件将组成产品。 这就是IDEA旗舰团队的工作方式，他们为自定义插件和*IntelliJ Platform*本身贡献代码。

当然，因为*IntelliJ Platform*是开源的，我们也接受[pull requests](https://github.com/JetBrains/intellij-community/pulls) 到平台本身， 而不是仅仅z爱这里查看代码而提交问题跟踪是通过[YouTrack](using the IDEA project)](https://youtrack.jetbrains.com/issues/IDEA), and if you wish to contribute to the platform, it is usually a good idea to open an issue describing the changes you wish to make before making the changes - this allows the team chance to give feedback and advice. More details can be found in the section on [Contributing to the IntelliJ Platform](/basics/platform_contributions.md).

## Rider

[Rider](https://www.jetbrains.com/rider/) uses the _IntelliJ Platform_ differently to other IntelliJ based IDEs. It uses the _IntelliJ Platform_ to provide the user interface for a C# and .NET IDE, with the standard IntelliJ editors, toolwindows, debugging experience and so on. It also integrates into the standard Find Usages and Search Everywhere UI, and makes use of code completion, syntax highlighting and so on.

However, it doesn't create a full PSI (syntactic and semantic) model for C# files. Instead, it reuses [ReSharper](https://www.jetbrains.com/resharper/) to provide language functionality. All of the C# PSI model, and all inspections and code rewriting, such as quick fixes and refactorings are run out of process, in a command line version of ReSharper. This means that creating a plugin for Rider involves two parts - a plugin that lives in the IntelliJ "front end" to show user interface, and a plugin that lives in the ReSharper "back end" to analyse and work with the C# PSI.

Fortunately, many plugins can simply work with the ReSharper backend - Rider takes care of displaying the results of inspections and code completion, and many plugins can be written that don't require an IntelliJ UI component. More details can be found in the Product Specific section.
