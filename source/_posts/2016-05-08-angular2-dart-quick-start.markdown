---
layout: post
title: "Angular2 Dart快速上手指南"
date: 2016-05-08 09:27:47 +0800
comments: true
categories: 翻译 dart angular2
---
注：本文翻译的是Angular2快速上手指南的Dart版本，转载请添加本文链接并标明出处。水平有限，仅供参考，更新更全的内容可以查看原文：https://angular.io/docs/dart/latest/quickstart.html。

___
<br/>
让我们从零开始用Dart来编写一个超级简单的Angular2应用。
（译注：Angular2支持TypeScript，JavaScript与Dart三种语言）

本篇教程假设你已经设置好[Dart SDK](https://www.dartlang.org/downloads/)及相关的开发工具。如果你还没有一个合适的编辑器，可以尝试一下拥有Dart插件的[WebStorm](https://confluence.jetbrains.com/display/WI/Getting+started+with+Dart)。当然，你也可以去官网的[工具页面](https://www.dartlang.org/tools/)下载各种IDE与编辑器的Dart插件。在配置好Dart SDK及你想要的开发工具后，再回到这里来。

## 准备新应用的目录

创建一个新文件夹，并在其中新建一个**pubspec.yaml**。(译注：在命令行下执行以下指令)

    > mkdir angular2_getting_started
    > cd angular2_getting_started
    > vim pubspec.yaml  # 这里使用vim，你可以使用任意其他你喜欢的编辑器！

在**pubspec.yaml**中，指定angular2跟browser作为项目依赖，当然也需要配置angular2 transformer。Angular2仍在变化中，所以我们使用一个指定的版本：2.0.0-beta.17。

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

在相同目录下，创建名为web的文件夹，并执行**pub get**安装angular2与browser（以及它们自身的依赖）。

    > mkdir web
    > pub get
    Resolving dependencies...

## 创建一个Dart文件
在**web**文件夹下创建一个**main.dart**。

    > vim web/main.dart  # 这里使用vim，你可以使用任意其他你喜欢的编辑器！

把以下内容粘贴到**web/main.dart**中：

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

这个组件是个空的，没有做任何事且名称为**AppComponent**的类。在你准备编写一个有实质内容的应用时，你可以为这个组件添加各种属性与相应的应用逻辑。

在这个类上面的是**@Component**注解，它告诉Angular这是一个组件。这里调用了**@Component**的构造函数，此函数有**selector**跟**template**两个命名参数。

**selector**参数指定了一个CSS选择器，它标明此组件依附一个名为**my-app**的自定义HTML元素。当Angular遇到一个**my-app**元素时，它就会创建并展示一个**AppComponent**类的实例。

**template**参数指定这个组件对应的模板，它告诉Angular如何去渲染视图。在我们的例子中，模板只是一行HTML文本："My First Angular 2 App"。

**main()**方法调用了Angular的**bootstrap()**函数，它告诉Angular以**AppComponent**为根元素启动应用。日后，这个应用的根元素上会添加更多的组件，以树状形式不断成长。

最开始的两行代码引人了两个Angular的库，所有使用Angular API的Dart文件都需要引人**core.dart**，而只有调用**bootstrap()**方法的Dart文件才需要引入**platform/browser.dart**。

## 创建一个HTML文件
创建一个名为**web/index.html**的文件并输入以下代码：

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

在**<body\>**中的**my-app**标签就是前面Dart文件中**selector**参数指定的自定义HTML元素。

## 运行 app
