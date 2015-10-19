---
layout: post
title: "Dart移动开发框架Flutter快速上手指南"
date: 2015-09-06 17:05:16 +0800
comments: true
categories: dart flutter
---
### 引言
[Flutter](http://flutter.io/)是Chromium项目组与Dart项目组合作开发的一个新的移动应用开发框架，虽然还处于初级阶段（版本号还处于0.0.X），但已经可以拿来写点简单的东西了。本文的内容就是让你了解如何配置flutter的开发环境，并编写一个简单的Hello World。

#### 注意:
* Flutter目前对ios开发的支持还不完善，所以本文将只以android开发来进行讲解。
* Flutter的应用打包功能也还没有完善，所以本文暂时不会对此进行讲解。
* Flutter目前要求Android 5.0或以上的设备才能进行开发调试，打包的apk最低支持Android 4.0（未确定）。
* 本文的操作都是在Mac下进行的，大致的流程应该也应该适用于Linux（flutter对Windows的支持将在不久后推出）。

## 开发环境配置

### 安装 Dart SDK
在Mac下用[Homebrew](http://brew.sh/)，Linux（Debian和Ubuntu）下通过apt-get，都可以方便的安装、升级Dart SDK，具体可以参考我写的文章 - [Dartlang实践：Dart SDK安装指南](http://jarontai.github.io/blog/2015/08/21/dart-sdk-auto-installtion/)。安装完成后，先确保在命令行下可以执行dart跟pub这两个指令，然后新建一个环境变量$DART_SDK，并将其指向Dart SDK的安装路径（通过homebrew安装的路径应该是：/usr/local/opt/dart/libexec/）。

### 安装 android-platform-tools
因为是进行android开发，自然需要安装adb（android debug bridge），你可以通过以下指令进行安装（只需要安装adb就可以，不需要完整的Android SDK）：
<!-- more -->

在Mac下使用homebrew安装：

    brew install android-platform-tools

Linux下使用apt-get：

    sudo apt-get install android-tools-adb

安装完成后，必须确保在命令行下可以顺利的访问adb指令。

### 准备安卓设备
准备一台系统版本是5.0或以上的android设备，按照以下指示进行操作：

* 开启开发者选项：进入“设置” > “关于手机”，连续点击“版本号”五次或以上
* 开启调试：进入“设置” > “开发者选项”，开启“USB调试”
* 连接电脑：用USB线将设备连接到电脑，手机弹出是否允许电脑调试对话框，选择允许

## Hello World
准备工作完成，现在正式开始编写代码。新建一个hello_world文件夹，并在其下创建一个文件pubspec.yaml，它的内容如下：

    name: hello_world
    dependencies:
      flutter: ">=0.0.6 <0.1.0"
    dev_dependencies:
      sky_tools: any

在项目文件夹下创建一个lib文件夹，然后在终端中进入项目根目录，执行pub get指令下载依赖，完成之后，项目的文件夹结构应该是类似于这样的：

    hello_world
      .pub
      .packages
      packages
      lib
      pubspec.lock
      pubspec.yaml


Flutter默认将lib/main.dart作为应用的入口文件，所以我们在lib文件夹下新建一个main.dart，并敲入以下代码：

{% codeblock lang:dart %}
import 'package:flutter/material.dart';

class HelloWorldApp extends StatelessComponent {
  Widget build(BuildContext build) {
    return new Center(
        child: new Text('Hello, world!',
            style:
                new TextStyle(color: new Color(0xFF01FFFF), fontSize: 25.0)));
  }
}

void main() {
  runApp(new HelloWorldApp());
}
{% endcodeblock %}

在我们的main方法中，一个HelloWorldApp组件被实例化，然后传入runApp方法中运行。HelloWorldApp的代码很简单，它构建了一个在屏幕居中显示的，指定了色彩跟文字大小的HelloWorld文本。如果你想学习更多有关widget的知识，请查看官方的[widget tutorial](https://flutter.io/tutorial/)。

## 运行
要运行调试我们编写的代码，必须先通过pub激活flutter。

进入命令行，执行以下指令：

    pub global activate flutter

此指令将指示pub下载flutter并将其置为全局可见。

进入项目目录，执行：

    flutter start

此指令将在设备上安装一个专门用于调试运行flutter应用的工具-SkyShell.apk，并把当前文件夹下的代码上传到SkyShell中运行。

如果你想让dart代码运行在checked模式，你可以这样：

    flutter start --checked

如果你想查看错误日志以及print函数所打印的信息，你可以另开一个终端执行：

    flutter logs

当然，也可以把指令合并起来执行：

    flutter start --checked && flutter logs

另外，如果不想一次次手动执行start指令，你可以这样（类似于web前端开发里面的livereload，只要文件一被修改，应用自动重新加载）：

    flutter listen

## 效果
检验成果的时候到了，运行效果如下：

  <img src="{{ root_url }}/images/custom/dart/sky/hello_world.png" />
  <img src="{{ root_url }}/images/custom/dart/sky/hello_world_landscape.png" />

运行效果没有什么惊喜，毕竟只是一个HelloWorld，等以后再写点更复杂的应用吧。

## 结语
虽然很多方面都还有待完善，但从整个Hello World的开发体验来讲，我个人认为，flutter比传统的android开发有了很大进步，它将很多web开发的“先进”理念带到了原生应用开发中，让人有“耳目一新”的感觉，希望flutter能够快速的成长起来，成为未来移动开发的中坚力量。

以上。

---
###更新记录
1. 2015.09.14 更改部分文字，更新官方的widget tutorial
2. 2015.09.24 注明Sky的版本
3. 2015.10.19 Sky => Flutter
