---
layout: post
title: "Dartlang译文：Dart语言概述"
date: 2015-05-04 17:34:20 +0800
comments: true
categories: 翻译 Dart Dart-Up-and-Running
---
  译注：本文是博主的原创翻译，转载请添加本文链接并标明出处。本文翻译的是Google Dart项目组撰写的《Dart：Up and Running》的第二章。文中存在一些新近出现、暂无标准翻译的技术向词语，已使用星号做了标注，在文章尾部附注可以查看它们的原文。博主的语文跟英语都很菜，如有翻译不妥或错误之处请多见谅。水平有限，本文仅作参考。
___
<br/>
  本章将向你展示如何使用Dart的各种特性，从变量、操作符到类、库等都会一一介绍。为了你能更好的学习本章，请确保你已经具备其他编程语言的使用经验。

  *注意*：为了尝试Dart的各种特性，请先在Dart Editor中创建一个命令行应用，具体步骤请参考上一章的[“走起”](http://jarontai.github.io/blog/2014/12/18/translation-dart-quick-start#up-and-running)。

  如果你需要更详尽的了解某个语言特性，请查阅[Dart语言规范](https://www.dartlang.org/docs/spec/)。

### 一个基本的Dart程序

{% codeblock lang:js %}
// 定义一个函数
printNumber(num aNumber) {
  print('The number is $aNumber.'); // 在终端中打印（输出）信息
}

// 程序从这里开始启动
main() {
  var number = 42; // 声明并初始化一个变量
  printNumber(number); // 调用一个函数
}
{% endcodeblock %}

以上代码使用的语言特性，在绝大部分Dart程序中都会用到，现在对它们逐一进行讲解：<!-- more -->

// 这是一个注释<br/>
使用 // 来表明本行接下来的文字都属于注释，或者，你也可以使用 /* ... */。更多详情，请查看[注释](#Comments)。

num<br/>
一个类型。Dart的部分内置类型：String，int以及bool。

42<br/>
一个数字字面量。字面量是一种编译时常量。

print()<br/>
一个打印输出信息的工具函数。

'...'（或者"..."）<br/>
一个字符串字面量。

$变量名（或者${表达式}）<br/>
字符串插值：在字符串字面量中包含一个变量或表达式，最终该变量或表达式的值将被替换显示（插入）到字符串常量中。更多详情，请查看[字符串](#Strings)。

main()<br/>
特殊的，必须的顶层函数，所有Dart程序都是从此函数开始运行。更多详情，请查看[main函数](#main-function)。

var<br/>
一种声明变量的方式，没有指定变量的类型。（译者注：类似于JavaScript的var）

  *注意*：我们的代码风格遵循[Dart风格指南](https://www.dartlang.org/articles/style-guide/)。例如：我们使用两个空格的代码缩进。

