[![官方的JetBrains项目](http://jb.gg/badges/official-flat-square.svg)](https://confluence.jetbrains.com/display/ALL/JetBrains+on+GitHub)

IntelliJ平台SDK文档
=======

这是
[IntelliJ平台SDK文档](http://www.jetbrains.org/intellij/sdk/docs/)
网站的仓库.

## 报告错误
请通过提交问题通知您在文档和样本中找到的任何内容不一致，过期的材料，美容问题和其他缺陷到[YouTrack](https://youtrack.jetbrains.com/issues/IJSDK). 

## 在本地使用网站
要检出并运行该网站的本地副本，请按照以下步骤操作。

### 前提

*  确保你有一个
   [git client](http://git-scm.com/downloads)
   客户端

*  这个网站需要
   [Ruby 2.0](https://www.ruby-lang.org/) 或者更高版本.
   遵循官方的
   [ruby语言](https://www.ruby-lang.org/en/downloads/)
   并且
   [安装](https://www.ruby-lang.org/en/documentation/installation/)
   Ruby在你的机器上。
   
*  这个网站需要 [Jekyll](http://jekyllrb.com/), 
  一个基于Ruby的网站生成框架.
   要安装Jekyll，请参考
   [安装指南](http://jekyllrb.com/docs/installation/).
   **提醒:** 如果你使用的是Windows，在安装Jekyll的时候可以面对一些特定的方面。
    参考 [在Windows上运行Jekyll指南](http://jekyll-windows.juthilo.com/) 获取更多信息。
   
### 导出网站仓库

要检查源代码，请运行以下命令:

```bash
git clone https://github.com/JetBrains/intellij-sdk-docs.git
```
   
### 初始化子模块

该网站使用JetBrains自定义网页模板。
要在本地启用自定义模板，您需要初始化存储库子模块。
在checkout目录中运行以下命令来执行此操作。
 
```bash
git submodule update --init --remote
```

### 建立和预览 
一套Rake任务，一个在Ruby中实现的Make-like程序，提供简短的命令来在本地构建和运行站点。

#### 根据源码构建站点
 
*  确保你在一个项目的根目录下
*  建立静态网站内容运行
   ```
   rake build
   ```
   
#### 预览

*  启动网络服务器运行
    ```
    rake preview
    ```
*  打开地址
   [http://localhost:4000/intellij/sdk/docs/](http://localhost:4000/intellij/sdk/docs/)
   在你的浏览器中。
   **注意:** 确保您在安装过程中没有更改默认的Jekyll端口。


