---
layout: post
title: "Dart移动开发框架sky快速上手"
date: 2015-09-06 17:05:16 +0800
comments: true
categories: dart sky
---
### 引言
[Sky](https://github.com/domokit/sky_engine)是Chromium项目组与Dart项目组合作开发的一个新的移动应用开发框架（平台），虽然还处于初级阶段（版本号还处于0.0.X），但已经可以用它写点简单的组件了。本文就将带你了解如何配置sky的开发环境，并编写一个简单的Hello World。在此过程中，你会发现，sky将很多web开发的“先进”模式带到了原生应用开发中，让人有“耳目一新”的感觉。

注意：
1. Sky现在对ios开发的支持还不够完善，所以本文将只会以android开发来进行讲解。
2. Sky目前要求Android 5.1或以上的设备才能进行开发调试，打包的apk最低支持Android 4.0。
3. Sky的应用打包也还没有完善，本文将不会对这块进行讲解（现有的代码都是在Sky Shell这个应用中运行）。
4. 虽然本文假定你使用的操作系统是Mac，但本文的主要流程应该也适用于Linux，Windows。

## 开发环境配置
### 安装 Dart SDK
在Mac下用Homebrew，Linux（Debian和Ubuntu）下通过apt-get，都可以方便的安装、升级Dart SDK，具体可以参考我写的文章：[Dartlang实践：Dart SDK安装指南](http://jarontai.github.io/blog/2015/08/21/dart-sdk-auto-installtion/)。安装完成后，请确保在命令行下可以执行dart跟pub这两个指令，而且还要新建一个环境变量$Dart_SDK，并将其指向Dart SDK的安装路径。

### 安装 android-platform-tools
因为是进行android开发，自然需要安装adb（android debug bridge），你可以通过以下指令进行安装：

注意：只需要安装adb就可以，不需要完整的Android SDK。

* Mac: brew install android-platform-tools
* Linux: sudo apt-get install android-tools-adb

### 准备安卓设备

Enable developer mode on your device by visiting Settings > About phone and tapping the Build number field five times.

Enable Android debugging in Settings > Developer options.

Using a USB cable, plug your phone into your computer. If prompted on your device, authorize your computer to access your device.
## Hello World

## 运行效果

以上。
