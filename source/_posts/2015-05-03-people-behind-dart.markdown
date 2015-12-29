---
layout: post
title: "Dartlang背后的那些大牛们"
date: 2015-05-12 11:23:39 +0800
comments: true
categories: dart 其他
---
最开始接触Dart，是想尝试一下除JavaScript外的浏览器编程语言（确切的说是以JavaScript为编译目标的语言，除Dart外，还有CoffeScript、TypeScript等）。在学习一段时间后，发现dart确实有很多优秀的语言特性，对它也越发喜欢了。最近，在好奇心驱使下，我开始搜索Dart项目组成员的相关资料。不查不知道，一查吓一跳，Dart项目组真算的上是藏龙卧虎。下面，我们就来介绍几位Dart项目组的主要成员：

你可能需要注意（也算是比较有趣）的一点：以下多位成员都有Java/JVM研发背景。

###Gilad Bracha
<img src="{{ root_url }}/images/custom/dart/people/Gilad.jpg" /><br/>
Gilad Bracha是一位经验丰富，专注于面向对象语言研究的专家。他曾经就职于[Sun][1]，专门从事Java/JVM规范的定制与实现工作。他不仅是Java语言规范第二、三版的合著者（co-author），也是JVM规范第二版的主要贡献者。在进入Google后，他加入了Dart项目组，他的主要工作就是Dart语言规范的编写。目前，Gilad正在编写一本全面介绍dart的书 - [The Dart Programming Language][10]。

<!-- more -->
###Lars Bak
<img src="{{ root_url }}/images/custom/dart/people/Lars.jpg" /><br/>
Lars Bak是Dart的联合创始人之一，他是一个来自丹麦的计算机天才，是一个虚拟机专家。他在近年主导开发的一个项目对互联网产生了深远影响，这就是Chrome的JavaScript虚拟机 - V8。而在更早以前，他从事Smalltalk与Java的虚拟机开发，他曾在[Sun][1]的HotSpot项目担任工程与技术主管，专职开发高性能的Java虚拟机。Lars Bak在虚拟机开发领域获得过惊人的成就，现在，他不仅要主导开发一个新的虚拟机，而且还有一门新的编程语言 - Dart。

###Kasper Lund
<img src="{{ root_url }}/images/custom/dart/people/Kasper.jpg" /><br/>
Kasper Lund也是Dart的联合创始人之一，他也来自丹麦。他早年跟Lars Bak都就职于Sun，一起从事JVM的开发。后来他跟Lars Bak一起加入Google，从事V8引擎开发。他主导开发V8引擎的Crankshaft项目，极大的提升了Chrome的JavaScript运行效率。最近，Kasper Lund开始主导开发[Fletch][2]，该项目可能是Dart在移动端发展的重要基础项目。

###Peter von der Ahé
<img src="{{ root_url }}/images/custom/dart/people/Peter.jpg" /><br/>
Peter是一个编译器专家，跟Lars Bak、Kasper Lund一样，早年也就职于Sun，他担任的职位是javac（Java的编译器）的技术主管。现在，他正专注于Dart增量编译的研发工作，同时他也在从事[Fletch][7]的开发。

###Kathy Walrath
<img src="{{ root_url }}/images/custom/dart/people/Kathy.jpg" /><br/>
Kathy Walrath是一位阅历丰富的技术写手，她曾就职于Sun、NeXT、HP等公司，她专注于Java文档编写长达11年。在加入Google后，她开始从事Chrome相关技术文档的编写。在web刚刚起步的那些年，她编写过Java applets的开发文档，而且她还是[The Java Tutorial][8]的合著者，并对其进行了多年的维护。如今，Kathy在Dart项目组从事各种技术文档的编写工作，她还和Seth Ladd合著了一本书：[Dart: Up and Running][9]。

###Bob Nystrom
<img src="{{ root_url }}/images/custom/dart/people/Bob.jpg" /><br/>
Bob曾是EA（艺电）公司的一名游戏开发工程师，而且写过一本关于游戏编程模式的畅销书 [Game Programming Patterns][3]。在加入Dart项目组后，他主导开发了Dart的包管理器 [pub][4]，而且也写了很多关于Dart的文章，其中包括深受开发者欢迎的[Dart编程风格指南][5]。而在最近，Bob开始帮助Dart建立DEP项目 - [Dart Enhancement Proposals][6]（Dart增强建议书），这将使Dart项目组能更好的接收、吸纳来自社区与开发者的建议。

###John McCutchan
<img src="{{ root_url }}/images/custom/dart/people/john.png" /><br/>

当John还没有本科毕业时，他就编写了[inotify][13]（Linux内核从2.6.13开始引入的系统事件监控框架），现在几乎所有主流的linux系统以及android都在使用它。在进入google前，他曾为索尼的游戏机部门工作多年，在那里他主要负责把[Bullet物理引擎][14]移植到PS3（索尼PlayStation游戏机的第三代）。在加入Dart项目组后，他主要负责开发调试与监控Dart应用的重要工具 - [Observatory][15]。

###Natalie Weizenbaum
<img src="{{ root_url }}/images/custom/dart/people/natalie.png" /><br/>

Natalie是Dart项目组中为数不多的女程序员，她是在前端开发中非常流行的CSS扩展语言[Sass][16]的主要贡献者。在Dart项目组中，她负责维护与开发众多基础性library，其中就包括 [pub][17], [test][18], [path][19]等。

###Konstantin Scheglov
<img src="{{ root_url }}/images/custom/dart/people/konstantin.jpg" width="200" height="200"/><br/>

Konstantin同样是一个有丰富Java开发背景的工程师，如果你曾经接触过Java GUI编程或是使用过Google的GWT，那你很有可能使用过他编写的工具 - Eclipse的[Windows Builder][20]插件, GWT的[GWT Designer][21]都出自于他之手。在加入dart项目组后，Konstantin主要从事Dart的IDE开发（Dart Editor），而在不久前，Dart项目组宣布不再提供默认的IDE，Konstantin也相应的转为主攻DAS开发（Dart Analysis Server - 它提供了一个分析dart代码的接口服务，使得Dart不再捆绑于某种IDE）。


*Dart项目组还有很多优秀的工程师，希望后面可以再补充。<br>
**以上信息大都收集整理自互联网，准确性有待商榷，如有错误之处，欢迎指正。


  [1]: http://zh.wikipedia.org/wiki/%E6%98%87%E9%99%BD%E9%9B%BB%E8%85%A6
  [2]: https://github.com/dart-lang/fletch
  [3]: http://gameprogrammingpatterns.com/
  [4]: https://pub.dartlang.org/
  [5]: https://www.dartlang.org/articles/style-guide/
  [6]: https://github.com/dart-lang/dart_enhancement_proposals
  [7]: https://github.com/dart-lang/fletch
  [8]: https://docs.oracle.com/javase/tutorial/
  [9]: https://www.dartlang.org/docs/dart-up-and-running/
  [10]: http://www.amazon.com/Dart-Programming-Language-Gilad-Bracha/dp/0321927702

  [13]: https://zh.wikipedia.org/wiki/Inotify
  [14]: http://bulletphysics.org/wordpress/
  [15]: https://dart-lang.github.io/observatory/
  [16]: http://sass-lang.com/
  [17]: https://github.com/dart-lang/pub
  [18]: https://github.com/dart-lang/test
  [19]: https://github.com/dart-lang/path

  [20]: https://eclipse.org/windowbuilder/
  [21]: https://developers.google.com/web-toolkit/tools/gwtdesigner/
