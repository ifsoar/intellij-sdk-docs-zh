---
title: Plugin Compatibility with IntelliJ Platform Products
---

<!--TODO link to sample_plugin file-->

All products based on IntelliJ Platform (IntelliJ IDEA, RubyMine, WebStorm, PhpStorm, PyCharm, AppCode, etc.) share the same underlying platform API. Thus, a plugin that does not use any Java-specific functionality may be marked as compatible with these other products in addition to IntelliJ IDEA. This is done by specifying *module dependencies* in the `plugin.xml` file.

A module dependency is a `<depends>` tag where the contents of the tag starts with `com.intellij.modules`.
 
For example:

```xml
<idea-plugin>
  ...
  <depends>com.intellij.modules.lang</depends>
  ...
</idea-plugin>
```

<!--TODO link to sample_plugin file--> 

If a plugin does not include any module dependency tags in its `plugin.xml`, it's assumed to be a legacy plugin and is loaded only in IntelliJ IDEA. 

If the `plugin.xml` includes one or more such tags, the plugin is loaded if the product contains all of the modules on which the plugin depends.

The following modules are currently available in all products based on IntelliJ Platform:

* `com.intellij.modules.platform`
* `com.intellij.modules.lang`
* `com.intellij.modules.vcs`
* `com.intellij.modules.xml`
* `com.intellij.modules.xdebugger`

The following modules are only available in specific products:

| Module                               | Product                                                               |
|--------------------------------------|-----------------------------------------------------------------------|
| `com.intellij.modules.java`          | IntelliJ IDEA, Android Studio                                         |
| `com.intellij.modules.ultimate`      | IntelliJ IDEA Ultimate Edition                                        |
| `com.intellij.modules.androidstudio` | Android Studio                                                        |
| `com.intellij.modules.appcode`       | AppCode                                                               |
| `com.intellij.modules.cidr.lang`     | AppCode, CLion                                                        |
| `com.intellij.modules.cidr.debugger` | AppCode, CLion, RubyMotion                                            |
| `com.intellij.modules.clion`         | CLion                                                                 |
| `com.intellij.modules.database`      | IntelliJ IDEA Ultimate Edition, DataGrip, PhpStorm, PyCharm, RubyMine |
| `com.intellij.modules.python`        | PyCharm                                                               |
| `com.intellij.modules.rider`         | Rider                                                                 |
| `com.intellij.modules.ruby`          | RubyMine                                                              |

PhpStorm does not have any modules specific to itself, but it includes the PHP plugin, which you can also use as a dependency: `com.jetbrains.php`

If you want to add a dependency to a specific plugin, then add a module dependency tag based on its plugin name/ID to the `plugin.xml`. For example `JavaScript` or `tslint`. Note that some plugins are not included by default in the target SDK, so you also have to add their jars manually to the SDKs classpath to compile against their provided classes. Make sure that you add the plugin jars to the SDK and not to your plugin, else the jars will be bundled with your plugin.

You can also specify optional module dependencies. If your plugin works with all products but provides some Java-specific functionality, you can use a dependency tag like this:

```xml
<depends optional="true" config-file="my-java-features.xml">
  com.intellij.modules.java
</depends>
```

Before marking a plugin as compatible with all products, you should verify that it doesn't use any APIs that are specific to IntelliJ IDEA. To do so, create an IntelliJ Platform SDK pointing to an installation of RubyMine, PyCharm, etc., compile your plugin against that SDK, and verify that everything compiles. Visit https://www.jetbrains.com/buy/opensource/ to check if your project is eligible for free Open Source Licenses of JetBrains products.

The [IntelliJ plugin repository](http://plugins.jetbrains.com/) automatically detects the products with which a plugin is compatible, based on the rules above, and makes it available to users of those products.

API of IntelliJ Platform and bundled plugins may be changed between releases. The major changes which may break plugins are listed on [Incompatible Changes in IntelliJ Platform and Plugins API](/reference_guide/api_changes_list.md) page.

