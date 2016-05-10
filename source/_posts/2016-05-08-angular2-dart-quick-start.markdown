---
layout: post
title: "Angular2 Dart快速上手指南"
date: 2016-05-08 09:27:47 +0800
comments: true
categories: 翻译 dart angular2
---
注：本文翻译的是Angular2快速上手指南的Dart版本，转载请添加本文链接并标明出处。水平有限，仅供参考，更新更全的内容请查看原文：[https://angular.io/docs/dart/latest/quickstart.html](https://angular.io/docs/dart/latest/quickstart.html)。

___
<br/>
让我们从零开始用Dart来编写一个超级简单的Angular2应用。
（译注：Angular2支持TypeScript，JavaScript与Dart三种语言，而据Dart项目组透露，Google内部几个大项目都在使用Dart版本的Angular2）

本篇教程假设你已经设置好[Dart SDK](https://www.dartlang.org/downloads/)及相关的开发工具。如果你还没有一个合适的编辑器，可以尝试一下拥有Dart插件的[WebStorm](https://confluence.jetbrains.com/display/WI/Getting+started+with+Dart)。当然，你也可以去官网的[工具页面](https://www.dartlang.org/tools/)下载各种IDE与编辑器的Dart插件。在配置好Dart SDK及你喜欢的开发工具后，再回到这里来。

## 准备新应用的目录

创建一个新文件夹，并在其中新建一个 **pubspec.yaml**。(译注：在命令行下执行以下指令)

    > mkdir angular2_getting_started
    > cd angular2_getting_started
    > vim pubspec.yaml  # 这里使用vim，你可以使用任意其他你喜欢的编辑器！

在 **pubspec.yaml** 中，指定angular2跟browser作为项目依赖，并对transformer也进行配置。因为Angular2的API还在变化，所以这里指定了一个版本：2.0.0-beta.17。(译注：指定使用某个版本可以避免多版本间的api冲突)

{% codeblock lang:yaml %}
name: angular2_getting_started
description: QuickStart
version: 0.0.1
environment:
  sdk: '>=1.13.0 <2.0.0'
dependencies:
  angular2: 2.0.0-beta.17
  browser: ^0.10.0
transformers:
- angular2:
    entry_points: web/main.dart
{% endcodeblock %}

<!-- more -->

在相同目录下，创建名为web的文件夹，并执行 **pub get** 安装angular2与browser（以及它们自身的依赖）。

    > mkdir web
    > pub get
    Resolving dependencies...

## 创建一个Dart文件
在 **web** 文件夹下创建一个 **main.dart**。

    > vim web/main.dart  # 这里使用vim，你可以使用任意其他你喜欢的编辑器！

把以下内容粘贴到 **web/main.dart** 中：

{% codeblock lang:js %}
import 'package:angular2/core.dart';
import 'package:angular2/platform/browser.dart';

@Component(selector: 'my-app', template: '<h1>My First Angular 2 App</h1>')
class AppComponent {}

main() {
  bootstrap(AppComponent);
}
{% endcodeblock %}

在以上代码中，你定义了一个Angular2 **component**（译注：组件），它是Angular2最重要的特性之一。组件是创建应用视图的主要方式，当然，它们需要应用逻辑的支持才能工作。

这个组件是个空的，没有做任何事且名称为 **AppComponent** 的类。在你准备编写一个有实质内容的应用时，你可以为这个组件添加各种属性与相应的应用逻辑。

在这个类上面的是 **@Component** 注解，它告诉Angular这是一个组件。这里调用了 **@Component** 的构造函数，此函数有 **selector** 跟 **template** 两个命名参数。

**selector** 参数指定了一个CSS选择器，它标明此组件依附一个名为 **my-app** 的自定义HTML元素。当Angular遇到一个 **my-app** 元素时，它就会创建并展示一个 **AppComponent** 类的实例。

**template** 参数指定这个组件对应的模板，它告诉Angular如何去渲染视图。在我们的例子中，模板只是一行HTML文本："My First Angular 2 App"。

**main()** 方法调用了Angular的 **bootstrap()** 函数，它告诉Angular以 **AppComponent** 为根元素启动应用。日后，这个应用的根元素上会添加更多的组件，以树状形式不断成长。

最开始的两行代码引入了两个Angular的库，所有使用Angular API的Dart文件都需要引入 **core.dart**，而只有调用 **bootstrap()** 方法的Dart文件才需要引入 **platform/browser.dart**。

## 创建一个HTML文件
创建一个名为 **web/index.html** 的文件并输入以下代码：

{% codeblock lang:html %}
<!DOCTYPE html>
<html>
  <head>
    <title>Getting Started</title>
    <link rel="stylesheet" href="styles.css">
    <script async src="main.dart" type="application/dart"></script>
    <script async src="packages/browser/dart.js"></script>
  </head>
  <body>
    <my-app>Loading...</my-app>
  </body>
</html>
{% endcodeblock %}

在 **<body\>** 中的 **my-app** 标签就是前面Dart文件中 **selector** 参数指定的自定义HTML元素。

## 运行应用
你有多种方式来运行你的应用，其中之一是在本地运行一个HTTP服务器并在[Dartium](https://www.dartlang.org/tools/dartium/)中查看应用。你可以使用任意你喜欢的服务器，比如WebStorm内置的服务器或者Python的SimpleHttpServer。

另外一种方式是通过执行 **pub serve** 来构建并启动应用，然后你就可以在任意现代浏览器中访问 http:\/\/localhost:8080 来查看你的应用。**Pub serve** 指令会实时的将Dart转换为JavaScript，当然，这会对页面的初次访问造成一定的延迟。

一旦应用运行起来，你就会浏览器窗口中看到 **My First Angular 2 App**。

如果你没有看到，请确保你正确输入了所有的代码并执行过 **pub get**。

## 生成JavaScript
在部署你的应用之前，你还需要生成JavaScript文件，**pub build** 指令使这项工作得以简单化。为了改善应用的性能，也需要使HTML文件直接引用生成的JavaScript，而这可以由 **dart_to_js_script_rewriter** 来完成。

将 **dart_to_js_script_rewriter** 添加到你的 **pubsepc.yaml** 中，注意 **dependencies** 跟 **transformers** 都需要设置。

{% codeblock lang:yaml %}
name: angular2_getting_started
description: QuickStart
version: 0.0.1
environment:
  sdk: '>=1.13.0 <2.0.0'
dependencies:
  angular2: 2.0.0-beta.17
  browser: ^0.10.0
  dart_to_js_script_rewriter: ^1.0.1
transformers:
- angular2:
    entry_points: web/main.dart
- dart_to_js_script_rewriter
{% endcodeblock %}

然后执行 **pub build**，将你的Dart代码编译为JavaScript。

    > pub build
    Loading source assets...

生成的JavaScript以及其他支持文件都会出现在 **build** 文件夹下。

当你为Angular应用生成JavaScript时，请确保使用Angular transformer。它会分析你的代码，将其中使用了反射的代码转换为静态代码，使Dart的构建工具输出更快速、体积更小的JavaScript。**pubspec.yaml** 中的高亮部分是对Angular transformer进行配置的，如下所示：(译注：这里高亮的是10、11、12行，笔者暂时没有找到使codeblock部分内容高亮的方法)

{% codeblock lang:yaml mark:1,5-8 %}
name: angular2_getting_started
description: QuickStart
version: 0.0.1
environment:
  sdk: '>=1.13.0 <2.0.0'
dependencies:
  angular2: 2.0.0-beta.17
  browser: ^0.10.0
  dart_to_js_script_rewriter: ^1.0.1
transformers:
- angular2:
    entry_points: web/main.dart
- dart_to_js_script_rewriter
{% endcodeblock %}

**entry_points** 指定了调用 **main()** 函数的Dart文件，如果需要查看更多相关信息，请查看[Angular transformer维基页面](https://github.com/angular/angular/wiki/Angular-2-Dart-Transformer)。

> #### 性能，transformer，以及Angular 2库
  当你引入 **bootstrap.dart**，你就引入了 **dart:mirrors**，这是一个反射库，它会影响生成的JavaScript的性能。但是别担心，Angular transformer会对你的入口（**pubspec.yaml** 中的 **entry_points**）执行转换操作，所以它们将不会使用 **dart:mirrors**。
