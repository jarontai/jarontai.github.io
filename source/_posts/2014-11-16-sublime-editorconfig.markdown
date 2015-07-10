---
layout: post
title: "SublimeText插件推荐：代码格式管家-EditorConfig"
date: 2014-11-16 21:28:19 +0800
comments: true
categories: 工具 Sublime
---
### 引言
  从大学毕业到现在，用过不少IDE与编辑器，记得起来的有：VisualStudio，Eclipse，NetBeans，SublimeText，Jetbrains家族（WebStorm，PhpStorm），VIM等。在这么多小伙伴中，用的最顺手的还是[SublimeText](http://www.sublimetext.com)（以下将简称为Sublime），它轻量，易用（对比VIM），跨平台，功能强大（对比其他编辑器，非IDE）。而Sublime丰富的第三方插件库，我认为是它优于其他编辑器的重要原因。接下来几篇博客，我将推荐一些我个人非常喜欢的插件。如果你还没有使用过SublimeText，你可以查看这篇[入门介绍](http://www.iplaysoft.com/sublimetext.html)。

### 简介
  今天要推荐的Sublime插件是：代码格式管家-EditorConfig，它最主要的功能是：同一项目代码在不同编辑器下能够保持统一的代码风格（主要是缩进）。此外，如果你不喜欢编辑器自带的默认风格（如sublime默认缩进宽度是4），那EditorConfig也可以帮到你。<!-- more -->
  
  注意：EditorConfig支持除Sublime之外的很多主流编辑器与IDE，如前面提到的VisualStudio, Eclipse, VIM, WebStorm等，它们都有对应的插件，插件的下载地址在EditorConfig主页可以找到：[http://editorconfig.org/](http://editorconfig.org/)。

### 插件的安装
  插件安装非常简单，使用Sublime命令面板的PackageControl:Install Package，搜索EditorConfig安装即可。
  <img src="{{ root_url }}/images/custom/sublime-install.png" />

### 插件的使用
  在项目根目录新建一个文件：.editorconfig（windows用户应该在文件管理器里面创建.editorconfig.文件，然后它会自动改名为.editorconfig），在此文件里填写你需要的格式规则，以下是一个典型的.editorconfig

{% codeblock lang:js %}
# http://editorconfig.org

root = true

[*]
# Change these settings to your own preference
indent_style = space
indent_size = 2

# We recommend you to keep these unchanged
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
{% endcodeblock %}

配置讲解：
<ul>
<li>第一行：是注释，所有的注释要以#或者;开头，且注释都要另起一行，即它们不能写在配置项的后面</li>
<li>第三行：root = true 是特殊配置项，必须放在本文件的开头（！？暂时没有理解官方网站的解释）</li>
<li>第五行：[*]是配置区域的开始标记，它下面的每一行配置项都属于此区域；括号里的字符表明此区域的作用范围，这里使用了星号通配符，表示以下配置将作用于所有文件；你可以使用通配符、路径及文件名等来指定范围，如：*，*.js，lib/*.php</li>
<li>第七行：indent_style 表示缩进的方式，可选项有：space - 每次输入tab会被空格代替；tab - 直接输入tab，不替换</li>
<li>第八行：indent_size 表示缩进的宽度（个数），可以自由设定你喜欢的宽度</li>
<li>第十一行：end_of_line 设置使用的换行符，有lf，cr，以及crlf，建议使用lf</li>
<li>第十二行：charset 设置文件的编码</li>
<li>第十三行：trim_trailing_whitespace 是否去除每行代码后的多余空格</li>
<li>第十四行：insert_final_newline 是否在每个文件尾部添加一个换行</li>
<li>第十六行：又一个配置区域，它的范围是所有后缀为md的文件</li>
<li>第十七行：跟十四行一样的配置项，此配置项会覆盖十四行（作用范围为所有的md文件）</li>
</ul>

以上配置项目，对风格影响最大的应该是indent_style跟indent_size，我个人目前遵循的是大多数js/node项目的风格：style为space，size为2。

更多详细的配置，请查看EditorConfig官网：[http://editorconfig.org/](http://editorconfig.org/)

以上。