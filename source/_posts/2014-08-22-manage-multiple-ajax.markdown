---
layout: post
title: "管理多个ajax请求(jQuery)"
date: 2014-08-22 21:30:18 +0800
comments: false
categories: js jQuery
---
  在web应用的开发中，我们可能会碰到需要发起多个ajax请求的情况。<br/>

  以下应该是最常见的写法:

{% codeblock lang:js %}
// Get html
$.get('/test', function(html) {

  // Get json data
  $.getJSON('/api/test.json', function(json) {
    
    // Get the JS
    $.getScript('/assets/test.js', function() {

       // display result
       $('.result').text(json.result);

       // Add html to page
       $('body').append(html);

    });

  });

});
{% endcodeblock %}

以上方法虽然可行，但是如果请求很多，就会产生不易维护的多层嵌套代码，而且请求是一个完了才执行下一个，效率不高。<br/><!-- more -->
___
<br/>

jQuery的ajax方法返回的对象都是[Deferred Object](http://api.jquery.com/category/deferred-object/), 可以使用[when](http://api.jquery.com/jQuery.when/)方法来处理它们。在when方法中，多个异步请求是并行处理的，且它返回的是promise对象，可以使用then或者done/fail方法来处理返回结果。

{% codeblock lang:js %}
$.when(
  // Get html
  $.get('/test'),

  // Get json data
  $.get('/api/test.json'),

  // Get JS
  $.getScript('/assets/test.js')

).then(function(data1, data2) {	// 成功回调，所有请求正确返回时被调用

  // All done
  // display result
  $('.result').text(data2[0].result);

  // Add html to page
  $('body').append(data1[0]);

}, function() { // 错误回调，任意一个请求失败后将被立即执行

	alert( '$.when failed!' );

});{% endcodeblock %}

如果所有请求正确返回，then方法的第一个回调将执行，如果有任意一个请求出错，第二个回调将被立即执行。需要注意的是每个请求的返回结果（如上所示的data1,data2），它们的类型是数组，里面的数据依次是: [ data, statusText, jqXHR ]。
___
<br/>
还有一种情况，如果请求个数是不确定的，那前面的做法就不太好处理了。而解决方法也很简单：利用js function的apply方法，将请求放在数组里面处理即可。

{% codeblock lang:js %}
var reqs = [];
reqs.push($.get('/test'));
reqs.push($.get('api/test.json'));
// 继续添加多个请求
...
...

$.when.apply($, reqs).then(function(data1, data2) {	// 成功回调，所有请求正确返回时被调用

  // All done
  // display result
  $('.result').text(data2[0].result);

  // Add html to page
  $('body').append(data1[0]);

}, function() { // 错误回调，任意一个请求失败后将被立即执行

	alert( '$.when failed!' );

});{% endcodeblock %}