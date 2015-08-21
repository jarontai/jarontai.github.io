---
layout: post
title: "Dartlang实践：Dart SDK安装指南"
date: 2015-08-21 14:24:01 +0800
comments: true
categories: dart
---
本文讲解了如何在不同平台上利用工具自动（非手动）安装Dart SDK，适合初次接触dartlang的开发者。

注意：因为安装过程中需要访问google的资源站点，请确保你能够访问google（科学上网）。

## Mac
个人认为Mac是从事dartlang开发的最佳平台，mac上的[homebrew](http://brew.sh/)又几乎是开发人员的标配，所以我们这里使用homebrew来安装Dart SDK。

### 安装
用homebrew安装Dart SDK是小菜一碟，你只要在终端中运行以下指令：

    $ brew tap dart-lang/dart
    $ brew install dart

如果是web开发者，你可能需要dartium（可以直接运行Dart的Chromium）, 那你可以这样：

    $ brew tap dart-lang/dart
    $ brew install dart --with-dartium
<!-- more -->
如果你想安装开发版本（dev channel）的Dart SDK，请添加 --devel

    $ brew install dart --devel

### 升级
使用homebrew安装了Dart SDK后，更新升级也变得非常简单：

    $ brew update
    $ brew upgrade dart

### 注意
在使用WebStorm或其他编辑器时，你可能需要知道Dart SDK的确切地址，你可以使用以下指令来查看相关信息：

    $ brew info dart

信息如下：

    dart-lang/dart/dart: stable 1.11.3, devel 1.12.0-dev.5.8
    https://www.dartlang.org/
    /usr/local/Cellar/dart/1.12.0-dev.5.0 (228 files, 34M)
      Built from source
    /usr/local/Cellar/dart/1.12.0-dev.5.8 (267 files, 37M) *
      Built from source
    From: https://github.com/dart-lang/homebrew-dart/blob/master/dart.rb
    ==> Options
    --with-content-shell
    	Download and install content_shell -- headless Dartium for testing
    --with-dartium
    	Download and install Dartium -- Chromium with Dart
    --devel
    	Install development version 1.12.0-dev.5.8
    ==> Caveats
    Please note the path to the Dart SDK:
      /usr/local/opt/dart/libexec

    --with-dartium:
      To use with IntelliJ, set the Dartium execute home to:
        /usr/local/opt/dart/Chromium.app

## Windows
Windows下有一个类似于homebrew的包管理器 - [chocolatey](https://chocolatey.org/)，通过它也可以便的安装Dart SDK。

在安装好chocolatey后，你只要运行一条指令即可完成安装；以下例子安装了1.11.0版本的Dart SDK与Dartium：

    choco install dart-sdk -version 1.11.0
    choco install dartium  -version 1.11.0

请访问chocolatey的[dart-sdk](https://chocolatey.org/packages/dart-sdk/)与[dartium](https://chocolatey.org/packages/dartium/)包页面以获取更多的信息。

## Linux
如果你使用的是Ubuntu/Debian，通过apt-get可以很方便的安装Dart SDK。

### 设置源
稳定版本

    $ sudo apt-get update
    $ sudo apt-get install apt-transport-https
    $ sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'
    $ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'
    $ sudo apt-get update

开发版本（替换前面的第四步）

    $ sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_unstable.list > /etc/apt/sources.list.d/dart_unstable.list'

### 安装
以下指令将安装当前可获取的最高版本的Dart SDK：

    $ sudo apt-get install dart

如果你同时设置了稳定版本跟开发版本，那以上指令将一直安装开发版本，因为开发版本的版本号肯定高于稳定版本。

### 安装特定版本
如果你同时设置了稳定版本跟开发版本，但是又想安装稳定版本，那你需要执行：

    $ sudo apt-get install dart/stable

如果你想安装某个特定版本，那你可以这样：

    $ sudo apt-get install dart=1.5.8-1
    $ sudo apt-get install dart=1.6.*
    $ sudo apt-get install dart=1.7.0-dev.0.1.*


以上。
