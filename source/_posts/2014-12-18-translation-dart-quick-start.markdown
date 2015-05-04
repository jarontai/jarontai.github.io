---
layout: post
title: "Dartlang译文：Dart快速入门"
date: 2014-12-18 12:07:36 +0800
comments: true
categories: 翻译 Dart Dart-Up-and-Running
---
  译注：本文是博主的原创翻译，转载请添加本文链接并标明出处。本文翻译的是Google Dart项目组撰写的《Dart：Up and Running》的第一章。文中存在一些新近出现、暂无标准翻译的技术向词语，已使用星号做了标注，在文章尾部附注可以查看它们的原文。博主的语文跟英语都很菜，如有翻译不妥或错误之处请多见谅。水平有限，本文仅作参考。
___
<br/>
  欢迎你来学习Dart！Dart是一个开源、开箱即用的（*1），专注于构建HTML5 web应用的开发平台。本文将告诉你Google为什么要创造Dart，Dart具有哪些酷炫的特性，以及如何编写、运行你的第一个Dart应用。
	
  Dart不仅是一门新的语言，它还提供了标准库、编辑器、虚拟机（VM）、一个能直接运行Dart的浏览器，以及将Dart代码编译为JavaScript的编译器。Dart立志成为一个更加高效的开发工具，能够开发出满足用户需求的，高性能的现代应用。

### Google为什么要创造Dart
  Google始终致力于使Web变得更好。我们（译者注：指Google，下同）编写了很多web应用，它们大都异常复杂，如：Gmail，Google Calendar，Google+等。我们希望web应用能快速加载、运行流畅、有趣而富有吸引力。我们想让不同知识背景的开发者都能够在浏览器上创建高质量的应用。<!-- more -->

  Google Chrome - 作为Google对推动web发展的贡献之一，是Google在web平台停滞不前的时期所创造的，它成功了！如下图所示，从2008年Chrome诞生开始，各家浏览器的速度都得到了极大的提升。

  注意：Chrome之所以能提供高速的web浏览体验，大都归功于它的JavaScript引擎 - V8。而现在，许多V8的工程师都投入到了Dart项目中。
  
  <img src="{{ root_url }}/images/custom/dart/chrome_browser_speed.png" />
  
  浏览器的新特性也在不断增加，比如：WebGL，FileSystem，Webworkers以及WebSockets等。浏览器也具备了自动更新能力，能够及时地向用户推送新的特性跟补丁。移动设备如平板电脑跟手机，也拥有了支持大部分HTML5特性的现代浏览器。

  虽然web平台有着上述非常多的改进，但开发者的体验却没有随之而改善。我们认为，在当前的web平台下，构建大型、复杂的web应用，还是非常麻烦的。趁手的web开发工具来的太慢，并且还远落后于其他开发平台。换个说法，也就是你需要熟知web开发的方方面面，才能为现代web开发应用。另外，虽然JavaScript引擎变得越来越快，但web应用的启动还是很慢。

  我们希望Dart能在以下两个方面改善web：

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* 更好的性能：作为虚拟机工程师，Dart的设计者知道怎样构建一门高性能的语言。一个结构更缜密的语言，更容易进行优化；而一个全新的虚拟机，也使得许多改进成为可能，比如：更快的启动速度。


  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* 更好的效率：对库及包的支持，使开发人员更容易与他人协作，更容易在不同项目共享代码。类型使得API更加清晰与易用。配套的工具也能帮助你检索、重构、调试代码。

### Dart初探
  闻名不如见面，以下是一小段Dart代码：

{% codeblock lang:js %}
import 'dart:math';

class Point {
  num x, y;
  Point(this.x, this.y);
  num distanceTo(Point other) {
    var dx = x - other.x;
    var dy = y - other.y;
    return sqrt(dx * dx + dy * dy);
  }
}

main() {
  var p = new Point(2, 3);
  var q = new Point(3, 4);
  print('distance from p to q = ${p.distanceTo(q)}');
}
{% endcodeblock %}

  当然，Dart的主要使用场景是编写现代web应用，为浏览器编程其实也很简单：

{% codeblock lang:js %}
import 'dart:html';

main() {
  var button = new ButtonElement();
  button..id = 'confirm'
        ..text = 'Click to Confirm'
        ..classes.add('important')
        ..onClick.listen((e) => window.alert('Confirmed!'));
  querySelector('#registration').children.add(button);
}
{% endcodeblock %}

  你将在第二章及第三章，更详细的学习Dart语言及它的标准库。（译者注：这里是指《Dart：Up and Running》的第二、三章）

### Dart的酷炫特性
  Dart的代码看起来似曾相识，但请不要被迷惑。Dart提供了许多新的特性，使你能更加高效的、充满乐趣的去构建下一代web应用。

  Dart简单易学，大部分开发者都可以快速学习它。它不仅有着熟悉的语法，还是一门拥有类、单继承、词法作用域、顶层函数等诸多特性的面向对象语言。许多开发者在数小时内就可以上手。

  Dart会被编译成JavaScript。为了使Dart兼容种类繁多的现代浏览器，Dart在最开始就被设计成能够编译为JavaScript的。Dart的每个特性，在被加入之前，都经过慎重考虑，因为必须确保它们能被编译成高效、符合逻辑的JavaScript代码。当然，Dart也有自己的底线，它不支持老土、过时的浏览器。

  Dart可以运行在客户端和服务器上。Dart虚拟机不仅能集成在浏览器中，还能够独立运行在命令行之上。Dart内置的标准库覆盖了文件、文件夹、套接字甚至web服务器等各个方面，你完全可以使用Dart来开发完全端到端（*2）的应用。

  Dart提供一个轻量的编辑器 - Dart Editor。你可以使用它来编写、运行以及调试Dart应用。Dart Editor提供代码自动完成、检测隐藏Bug、调试命令行及web应用，乃至重构等诸多功能。Dart Editor并不是编写Dart应用的必需品，它只是让你能更快更好的进行编码。（译者注：WebStorm、Sublime Text等都有Dart插件）

  Dart支持类型，但不强制使用。当你想进行快速开发，或者代码的结构还没有确定，又或者你觉得现有类型无法满足你的需求，你都可以省略类型。当你的应用开始成形，代码的结构变得清晰，其他开发者也慢慢加入时，你就可以给代码添加类型了。Dart的可选类型是静态的注解，能够作为代码的文档，清晰的表达你的意图。使用类型意味着你能节省不少代码注释，而开发工具也能提供更好的警告与错误信息。

  Dart能胜任小至简单脚本，大到复杂应用。Web开发其实是一个迭代的过程。有浏览器的重新加载按钮充当编译器，编写web应用原型只需要你编写几个函数就搞定了，这在某种程度上成了一种乐趣。当你的想法更加成熟时，就可以添加更多的代码与逻辑。得益于Dart对顶层函数、可选类型、类与库的支持，你的应用可以不断成长。代码不断进化，而Dart Editor这样的工具，可以帮助你对它们进行检查、重构。

  Dart有非常多的内置标致库。核心库支持内置类型以及其他基础特性，如：集合、日期及正则表达式等。HTML库则用来编写web应用，它像我们熟悉的DOM编程，只是为Dart做了优化。命令行应用可以使用I/O库来操作文件、文件夹、套接字、服务器等等。其他库还包括了URI、UTF、Crypto、Math以及Unit test等。

  Dart使用isolates（*3）来支持安全而简便的并发编程。传统的线程是共享内存的，它们难于调试并可能导致死锁。而Dart的isolates，受Erlang的启发，使用了一个更简单易懂的模式来运行并发且被隔离的代码。isolates的创建过程低耗、快速，而且没有状态信息被共享。

  Dart支持代码共享与复用。传统的web开发不能方便的整合第三方代码。使用Dart的包管理器（pub）和库等特性，你可以轻松的搜索、安装、集成来自互联网及其他公司的代码。

  Dart是开源的。Dart是为web而生的，它使用类似BSD的协议。你可以在线查看Dart项目的[源码以及Bug](https://code.google.com/p/dart/)。或许你下次可以提交一个补丁呢？

### <a name="up-and-running"></a>走起（*4）
  现在你应该对Dart有了大概的了解，是时候写代码了。以下的操作都是使用开源的编辑器Dart Editor。在你下载完Dart后，你不仅拥有了Dart Editor，还获得了Dart转JavaScript编译器，以及一个内置了Dart虚拟机的定制版Chromium（昵称为Dartium）。

  注意：如果在安装使用Dart Editor时碰到问题，请查看[Dart Editor故障排查](https://www.dartlang.org/tools/editor/troubleshoot.html)。

#### 步骤1：下载安装软件包
  在此步骤中，你将安装Dart Editor。如果你没有安装Java，就还要安装Java运行环境。（如果你不想修改环境变量，你可以把JRE直接放到你的Dart安装目录下，注意文件夹名称必须是jre）

1. 下载[Dart与Dart Editor](https://www.dartlang.org/tools/download.html)
2. 将你下载的文件解压，得到一个文件夹，我们把它称为Dart的安装目录。这个文件夹里面包含了Dart Editor执行文件以及其他子文件夹。
3. 如果你没有安装Java，请去下载并安装它。Dart Editor需要Java 6或以上的版本才能运行。

#### 步骤2：启动编辑器
  进入Dart安装目录，双击DartEditor执行文件<img src="{{ root_url }}/images/custom/dart/dart_logo.png" />。

  你应该会看到Dart Editor的应用窗口被打开，就像下面这张图一样：
  <img src="{{ root_url }}/images/custom/dart/dart_editor_open.png" />

#### 步骤3：运行demo
  Dart Editor附带了不少demo。在此步骤中，你将打开一个web应用，并让它在Dartium中运行。

1. 点击**Welcome**选项卡，或是从**Tools**菜单中选择**Welcome Page**。
2. 进入Welecome选项卡，点击标题为**Sunflower**的图片。Dart Editor将会创建一份[Sunflower app](https://github.com/dart-lang/sample-sunflower)的拷贝，编辑区则会显示web/sunflower.dart文件的内容。
3. 点击Run按钮<img src="{{ root_url }}/images/custom/dart/run_button.png" />。Dart Editor会打开Dartium，并使其加载sunflower.html文件。（**注意**：Dartium还处于技术预览期，它在安全性与稳定性方面，存在一定的问题，所以请不要使用Dartium作为你的主要浏览器。）
4. 使用页面上的滑块来改变太阳花的形状，如下图：
  <img src="{{ root_url }}/images/custom/dart/slider_sunflower.png" />

#### 步骤4：创建并运行一个应用
  从头开始创建一个简单的web或命令行应用是非常简单的。以下步骤将带你创建运行一个命令行应用：

1. 点击新建应用按钮<img src="{{ root_url }}/images/custom/dart/app_new_button.png" />（它位于Dart Editor的左上角），或者是选择**File > New Application**菜单项，又或者是点击**Welcome**选项卡里面的**Create an Application...**按钮。一个对话框将会弹出（参见下图）。
2. 填写应用的名称，比如：hello_world。如果你不喜欢默认保存路径，请填写一个新的路径或者选择一个新的目录。
3. 请确保**Generate sample content**与**Command-line application**是被选中的。然后点击**Finish**，完成新建过程。

  <img src="{{ root_url }}/images/custom/dart/app_new_dialog.png" />

  默认创建的Dart文件将在编辑区被打开，它所在文件夹也显示在文件视图区。此时，你的Dart Editor应该类似于下图：

  <img src="{{ root_url }}/images/custom/dart/app_init.png" />

4.点击Run按钮<img src="{{ root_url }}/images/custom/dart/run_button.png" />运行你新编写的应用。对命令行应用来说，print()函数产生的输出将展现在Dart Editor的底部右侧，位于**Problems**选项卡旁边的某个选项卡中。

译文结束。
更新于：2015-05-04

___
<br/>
附注：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*1 batteries-included <-> 开箱即用 (参考了知乎 - http://www.zhihu.com/question/24710451)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*2 full end-to-end <-> 完全端到端 (无知翻译)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*3 isolates (未翻译)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*4 up and running <-> 走起 (逗比翻译)

---
<br/>
本文地址：http://jarontai.github.io/blog/2014/12/18/translation-dart-quick-start/<br/>
原文地址：https://www.dartlang.org/docs/dart-up-and-running/ch01.html