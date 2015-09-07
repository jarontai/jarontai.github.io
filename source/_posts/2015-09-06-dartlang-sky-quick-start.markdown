---
layout: post
title: "Dart移动开发框架SKY快速上手指南"
date: 2015-09-06 17:05:16 +0800
comments: true
categories: dart sky
---
### 引言
[Sky](https://github.com/domokit/sky_engine)是Chromium项目组与Dart项目组合作开发的一个新的移动应用开发框架（平台），虽然还处于初级阶段（版本号还处于0.0.X），但已经可以用它写点简单的东西了。本文就将带你了解如何配置sky的开发环境，并编写一个简单的Hello World。在此过程中，你会发现，sky将很多web开发的“先进”模式带到了原生应用开发中，让人有“耳目一新”的感觉。

#### 注意:
* Sky现在对ios开发的支持还不完善，所以本文将只会以android开发来进行讲解。
* Sky的应用打包功能也还没有完善，所以本文将不会对此进行讲解（现有代码都是在Sky Shell中运行）。
* Sky目前要求Android 5.1或以上的设备才能进行开发调试，打包的apk最低支持Android 4.0（不确定）。
* 虽然本文的操作都是在Mac下进行的，但大致的流程应该也适用于Linux，Windows。

## 开发环境配置
### 安装 Dart SDK
在Mac下用[Homebrew](http://brew.sh/)，Linux（Debian和Ubuntu）下通过apt-get，都可以方便的安装、升级Dart SDK，具体可以参考我写的文章 - [Dartlang实践：Dart SDK安装指南](http://jarontai.github.io/blog/2015/08/21/dart-sdk-auto-installtion/)。安装完成后，先确保在命令行下可以执行dart跟pub这两个指令，然后新建一个环境变量$DART_SDK，并将其指向Dart SDK的安装路径（通过homebrew安装的路径应该是：/usr/local/opt/dart/libexec/）。

### 安装 android-platform-tools
因为是进行android开发，自然需要安装adb（android debug bridge），你可以通过以下指令进行安装：

注意：只需要安装adb就可以，不需要完整的Android SDK。

* Mac: brew install android-platform-tools
* Linux: sudo apt-get install android-tools-adb

### 准备安卓设备
准备一台系统版本是5.1或以上的android设备，按照以下指示进行操作：

* 开启开发者选项：进入“设置” > “关于手机”，连续点击“版本号”五次或以上
* 开启调试：进入“设置” > “开发者选项”，开启“USB调试”
* 连接电脑：用USB线将设备连接到电脑，手机弹出是否允许电脑调试对话框，选择允许

## Hello World
准备工作完成，现在正式开始编写代码。新建一个hello_world文件夹，并在其下创建一个文件pubspec.yaml，它的内容如下：

    name: hello_world
    dependencies:
      sky: any
      sky_tools: any

在项目文件夹下再创建一个lib文件夹，然后在终端中运行pub get，并等待pub下载sky、sky_tools等依赖。在pub get完成之后，你的项目结构应该是类似于这样的：

    hello_world
      .pub
      .packages
      lib
      packages
      pubspec.lock
      pubspec.yaml


Sky默认使用lib/main.dart作为应用入口，所以我们在lib文件夹下新建一个main.dart，并敲入以下代码：

{% codeblock lang:dart %}
import 'package:sky/widgets.dart';

class HelloWorldApp extends App {
  Widget build() {
    return new Center(child: new Text('Hello, world!'));
  }
}

void main() {
  runApp(new HelloWorldApp());
}
{% endcodeblock %}

Execution starts in main, which in this example runs a new instance of the HelloWorldApp. The HelloWorldApp builds a Text widget containing the traditional Hello, world! string and centers it on the screen using a Center widget. To learn more about the widget system, please see the widgets tutorial.
## 运行效果

以上。
