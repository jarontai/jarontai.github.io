---
layout: post
title: "Dartlang译文：Dart快速上手指南"
date: 2014-12-18 12:07:36 +0800
comments: false
categories: 翻译 Dart
---
  译者注：本文欢迎转载，请添加本文链接并标明出处。文中存在的一些新近出现、不好翻译且暂无翻译标准的技术名词，都用星号进行了标注，在附注部分可以查看它们的原文。水平有限，本文仅供参考。
___
<br/>
  欢迎来学习Dart！Dart是一个开源的、高效的（*1），用于构建HTML5 web应用的开发平台。本文将告诉你为什么Google要创造Dart，Dart有哪些酷炫的特性，以及如何编写、运行你的第一个Dart应用。
	
  Dart不仅是一门新的语言，它还有标准库、编辑器、虚拟机（VM）、能直接运行Dart的浏览器（Dartium）以及一个将其编译为JavaScript的编译器。Dart立志于成为一个超乎想象的、高效的、用于构建高性能现代应用的开发工具。

### 为什么Google要创造Dart
  Google关注于如何使Web变得更好。我们编写了很多web应用，它们大都异常复杂，比如：Gmail，Google Calendar，Google+等。我们希望web应用能加载迅速、运行流畅、有趣而富有吸引力。我们想让不同背景的开发者都能够在浏览器上创建高质量的应用。<!-- more -->

  Google Chrome，作为Google对web的贡献之一，是Google在web平台看似停滞不前的时期创造了它。它成功了！如下图所示，从2008年Chrome诞生开始，浏览器的速度得到了极大的提升。

  注意：Chrome之所以速度快，大都归功于JavaScript引擎V8。如今，许多V8的工程师都投入到了Dart项目中。
  <img src="{{ root_url }}/images/custom/dart/chrome_browser_speed.png" />
  
  浏览器的新特性也在不断增加，比如：WebGL，FileSystem，Webworkers以及WebSockets等。浏览器已经具备自动更新能力，能够及时地向用户推送新的特性跟补丁。移动设备像平板电脑跟手机，也拥有支持大部分HTML5特性的现代浏览器。

  虽然web平台有着上述非常多的改进，但是开发者的体验却并没有随之而改善。我们认为构建大型的、复杂的web应用，不应该像现在那么麻烦的。趁手的web开发工具来的实在太慢，并且还是落后于其他开发平台。其实，你不应该非得熟练掌握web编程之后，才能为现代web创建应用的。而且，虽然JavaScript引擎变得越来越快，但web应用的启动还是很慢。

  我们希望Dart在以下两个方面发挥作用：

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* 更好的性能：作为VM（虚拟机）工程师，Dart的设计者知道怎样构建一门高效的语言。一个结构严密的语言更容易优化，一个全新的虚拟机使得许多改进成为可能，例如：更快的启动速度。


  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* 更好的效率：对库（libraries）及包（packages）的支持，使你更容易与他人协作，更容易在不同项目共享代码。类型（Types）使得API更加清晰与易用。配套的工具也能够帮助你检索、重构、调试代码。

### Dart初探
  闻名不如见面，以下是一小段Dart代码

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

  当然，Dart的主要使用场景就是构建现代web应用，为浏览器编程很简单：

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

  你将在第二章及第三章，更详细的学习Dart语言及它的标准库。

### Dart的酷炫特性
  Dart看起来似曾相识，但请不要被迷惑了。Dart提供了许多新特性，使你更加高效的、充满乐趣的去构建下一代web应用。

  Dart简单易学，大批的开发者都能快速学习它。它是一门有着非常熟悉的语法的，使用类、单继承、词法作用域、顶层函数的面向对象语言。大部分开发者在数小时内就可以上手。

  Dart会被编译成JavaScript。Dart在最开始就被设计成能够编译为JavaScript，这样才能使Dart应用能够运行在不同的现代浏览器中。Dart的每个特性，在被加入之前，都经过慎重考虑，以确保它们能被编译成高效的、符合逻辑的JavaScript代码。Dart也有自己的底线，它不支持老土的、过时的浏览器。

  Dart可以运行在客户端与服务器上。Dart虚拟机不仅能集成在浏览器中，还能够独立运行在命令行之上。Dart内置的标准库覆盖了文件、文件夹、套接字甚至web服务器等各个方面，你完全可以使用Dart来开发完全端到端（*2）的应用。




___
<br/>
附注：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*1 高效的  batteries-included<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*2 完全端到端  full end-to-end



---
本文地址：http://jarontai.github.io/blog/2014/12/18/translation-dart-quick-start/<br/>
译文地址：https://www.dartlang.org/docs/dart-up-and-running/ch01.html