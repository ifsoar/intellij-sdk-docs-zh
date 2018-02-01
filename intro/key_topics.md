---
title: 关键主题
---

*IntelliJ Platform*非常大，功能非常强大，它的大小和范围最初可能非常艰巨。 本页旨在列出插件作者感兴趣的关键主题，并提供到最常用的扩展点的快速链接。

## 基本概念

- 插件[入门](/basics/getting_started.md).
- [测试插件](/basics/testing_plugins.md).
- [结构概述] - _IntelliJ Platform_的不同层次的简要介绍。
- 组件模型 - _IntelliJ Platform_是一个基于组件的应用程序，负责创建组件和注入依赖关系。 理解这是建立插件所必需的。
- 扩展点 - 如何使用扩展点注册组件，以及如何找出可用的扩展点。
- [抽象文件](/basics/architectural_overview/virtual_file.md) - 所有的文件访问应该通过虚拟文件系统来抽象和缓存文件系统。 这意味着您可以使用本地文件系统上的文件，zip文件或版本控制的旧版本。
- [扩展点](/basics/plugin_structure/plugin_extensions_and_extension_points.md)

## 代码模型

_IntelliJ Platform_的代码模型被称为PSI - 程序结构索引。 PSI解析代码，建立索引并创建语义模型。

## 常见的扩展点

_IntelliJ平台_是非常可扩展的，大多数功能和服务可以扩展。 一些常见的扩展点是：

* [Actions](/tutorials/action_system.md) - 菜单和工具栏
* [代码检查](/tutorials/code_inspections.md) - 代码分析，查看语法树和语义模型，并在编辑器中突出显示问题。
* [意向](/tutorials/code_intentions.md) - 当文本插入符号位于特定位置时，在<kbd> Alt </kbd> + <kbd> Enter </kbd>菜单中可用的上下文特定操作。
* [代码完成](/reference_guide/custom_language_support/code_completion.md).
