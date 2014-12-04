---
layout: post
title: "用iFrame Resizer解决iframe高度自适应问题"
date: 2014-07-25 20:45:39 +0800
comments: false 
categories: js HTML5
---
  最近工作中需要对一个旧项目进行改造，不得已使用了让人头疼的iframe，碰到的最大问题是没有好的方法使其高度自适应。Google一番之后，发现[iframe-resizer](http://davidjbradshaw.github.io/iframe-resizer/)能够比较好的解决这个问题，而且还支持跨域访问（使用[postMessage](https://developer.mozilla.org/en-US/docs/Web/API/window.postMessage)）。
    
  在使用它之前，必须明确iframe resizer要求IE8+（firefox，chrome等自然没有问题），如果你需要支持旧版本IE，请关掉本页然后再去google。其次，iframe resizer提供了原生JS与jQuery插件两种调用方式，<!-- more -->而原生方式需要[额外的配置](http://davidjbradshaw.github.io/iframe-resizer/#browser-compatibility)，所以我推荐选择jQuery插件方式（毕竟jQuery几乎是标配了）。  
  
  ___
  
  OK，下载iframe resizer。

  在iframe resizer压缩包的js文件夹中，有两个文件：
  第一个js是：iframeResizer.min.js。这个js是要放在需要嵌入iframe的页面（parent）中，其调用方式如下（一般情况下你不需要传递任何参数即可实现高度自适应，详细参数请参考[官网](http://davidjbradshaw.github.io/iframe-resizer/#options)）：

{% codeblock lang:js %}
$('iframe').iFrameResize([{log: true}]);
{% endcodeblock %}

  第二个js是：iframeResizer.contentWindow.min.js，它需要放到你的iframe页面(child)中去，注意只要引人，不需要代码配置。
  ***
  
  接下来是设置iframe，需要注意的是width必须是百分比，scrolling设置为no（为了兼容性）。

{% codeblock lang:html %}
<iframe src="http://yourserver.com/index.html" width="100%" scrolling="no"></iframe>
{% endcodeblock %}
  
  当然，你也可以使用document.createElement来动态创建它。
{% codeblock lang:js %}
var iframe = document.createElement('iframe');
iframe.setAttribute('src', 'http://yourserver.com/index.html');
iframe.setAttribute('width', '100%');
iframe.setAttribute('scrolling', 'no');
document.body.appendChild(iframe);
{% endcodeblock %}

  ***
  
  按照以上步骤设置，基本上就能够解决iframe自适应问题，且iframe内容可跨域。
 