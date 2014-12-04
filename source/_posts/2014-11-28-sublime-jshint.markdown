---
layout: post
title: "SublimeText插件推荐：JS错误检查工具 - JSHint与JSHint Gutter"
date: 2014-11-28 09:46:58 +0800
comments: true
categories: 工具 Sublime
---
  注意：如果你是Windows用户，本文文字或图片中出现的某些指令如：which，是无法在windows命令行下运行的，你可以安装Git for windows, 其附带的Git Bash可以运行大多数的Bash命令。
___
<br/>
### 引言
  我喜欢使用SublimeText（以下将简称为Sublime）来写JavaScript，但有时候代码量一多，难免会犯些小错误，比如变量名写错，多了一个括号等等；而Sublime是编辑器，本身没有代码检查功能，只有当JS代码在浏览器里运行报错了，才发现问题，而这样就会浪费不少的时间。所以，我就想找找有没有这样的插件，使Sublime能够检测基本的JS语法错误。经过一番搜索后，终于找到了，而这也是今天要介绍的：JS错误检查工具 - JSHint与JSHint Gutter。<!-- more -->

### 简介
  JSHint是一个JS代码质量(错误)检查工具，它不但能检查JS代码的语法错误，还能够监控代码质量，很多公司跟开源项目都在使用它，比如：Facebook、jQuery、Bootstrap等等。在Github上，使用JSHint的项目多如牛毛，如果你在某个项目里面，发现有.jshintrc文件，那它就使用了JSHint。JSHint是一个独立的工具，它不直接提供对Sublime的支持，它本身只提供命令行工具（基于NodeJS）。我们可以使用JSHint Gutter这个插件，它能够调用JSHint执行代码检查，然后将结果显示到Sublime界面上。
  
  注意：除Sublime之外的很多编辑器与IDE，也都有配套的JSHint插件，它们的下载链接请查看 [http://www.jshint.com/install/](http://www.jshint.com/install/)。

### 安装JSHint
  请先安装好[NodeJS](http://nodejs.org/)，然后在终端/命令行中输入 npm install -g jshint

  安装过程类似下图
  <img src="{{ root_url }}/images/custom/jshint-m.png" />

### 安装与配置JSHint Gutter
  JSHint Gutter安装更加非常简单，使用Sublime命令面板的PackageControl:Install Package，搜索安装即可。

  安装完成后，在Sublime的Package Settings里找到JSHint Gutter，选择Set Plugin Options：
  <img src="{{ root_url }}/images/custom/sublime-jshint-menu.png" />
  
  设置NodeJS执行文件所在的路径（node_path），并将lint_on_save（文件保存时检查）选项打开
  <img src="{{ root_url }}/images/custom/sublime-jshint-setting.png" />

  请注意：不同的操作系统，不同的安装工具（我使用nvm安装node），node执行文件所在的路径都不一样，你可以使用 which node 来查看

### 设置.jshintrc
  在项目根目录新建一个文件：.jshintrc（windows用户应该在文件管理器里面创建.jshintrc.文件，然后它会自动改名为.jshintrc），在此文件里填写你的检查规则，以下是一个典型的.jshintrc

{% codeblock lang:js %}
{
  "curly": true,
  "eqeqeq": true,
  "immed": true,
  "noarg": true,
  "noempty": true,
  "quotmark": "single",
  "undef": true,
  "unused": true,
  "node": true
}
{% endcodeblock %}

配置讲解(配置选项 true表示打开，false表示关闭)：
<ul>
<li>第二行：curly 表示所有的代码块必须使用大括号</li>
<li>第三行：eqeqeq 表示判断相等时，必须使用 ===</li>
<li>第四行：immed 表示立即执行函数必须用括号包起来 `(function () { } ());`</li>
<li>第五行：noarg 表示禁止使用 `arguments.caller` 和 `arguments.callee`</li>
<li>第六行：noempty 表示禁止出现空的代码块 `{ }`</li>
<li>第七行：quotmark 是引号的使用规则，有以下四个选项
<ul>
<li>      false : 不检查</li>
<li>      true : 检查一致性（要么都是单引号，要么都是双引号）</li>
<li>      single : 必须都是单引号</li>
<li>      double : 必须都是双引号</li>
</ul>
</li>
<br>
<li>第八行：undef 表示所有的局部变量都必须先声明再使用</li>
<li>第九行：unused 表示禁止变量已经声明，但却不使用</li>
<li>第十行：node 表明你的项目是NodeJS项目，require等node特有的全局函数将通过检查</li>
</ul>

以上只是少数常见的配置项目，请到官网查看完整项目列表：[JSHint Options](http://www.jshint.com/docs/options/)

### 使用效果
  我故意在代码里多添加了一个括号，然后保存文件，错误提示马上出现了，点击红色的错误标记，在底部信息栏会出现提示信息。
  <img src="{{ root_url }}/images/custom/sublime-jshint-action.png" />

  哈哈，以后用Sublime写JavaScript会更加顺手了。Sweet！

以上。