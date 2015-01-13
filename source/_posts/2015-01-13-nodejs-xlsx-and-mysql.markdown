---
layout: post
title: "Node.js实践：读取Excel，查询MySQL"
date: 2015-01-13 09:10:55 +0800
comments: true
categories: nodejs
---
  注意：本文假设你对JavaScript异步编程，Node.js，MySQL数据库等有基本的了解。本文中大部分操作都是基于Mac OS的终端（Windows环境推荐使用Git附带的[Git Bash](https://msysgit.github.io/)）。
### 需求
  假设有个小需求：提供一个Excel文件（xlsx格式），其中含了用户数据，你需要查询MySQL数据库，把其中没有验证邮箱的用户给筛选出来。

  Excel数据格式如下（第一行为标题）：<br>
  <img src="{{ root_url }}/images/custom/20150113/excel-data.png" />

  数据库用户表（users）关键字段：username, email_activation（0表示未激活，1表示已激活）；

### 准备
  为了应对这个任务，我们使用了三个package，分别是：[xlsx](https://www.npmjs.com/package/xlsx), [mysql](https://www.npmjs.com/package/mysql), [async](https://www.npmjs.com/package/async)。从它们的名字可以看出它们各自的功能，xlsx负责读写xlsx文件，mysql负责连接查询数据库，async则用来简化异步代码。
  <!-- more -->

  新建一个项目文件夹member_filter，进入后执行npm init，简单填写项目信息，然后安装我们需要的三个依赖：npm install xlsx mysql async --save

  <img src="{{ root_url }}/images/custom/20150113/setup1.png" />
  <img src="{{ root_url }}/images/custom/20150113/setup2.png" />

### 编码
  代码的思路：读取xlsx文件里面的用户数据，对其进行适当的转换处理，然后再用这些数据去MySQL数据库查询，得到邮箱没有被激活的用户并将它们打印出来。

{% codeblock lang:js %}
// 导入依赖
var XLSX = require('xlsx');
var async = require('async');
var mysql = require('mysql');

// 读取xlsx文件，将第一个worksheet转换成json对象
var workbook = XLSX.readFile('test.xlsx');
var sheetNameList = workbook.SheetNames;
var worksheet = workbook.Sheets[sheetNameList[0]];
var userAarray = XLSX.utils.sheet_to_json(worksheet);

// 连接MySQL
var connection = mysql.createConnection({
  host     : 'localhost',
  user     : 'root',
  password : 'root',
  database : 'test'
});
connection.connect();

// 通过async遍历用户对象数组，循环异步查询MySQL，检查email是否激活
var sql1 = 'SELECT 1 FROM users WHERE username = ';
var sql2 = ' AND email_activation = 1';
var counter = 0;
var key = '账号';
async.eachSeries(userAarray, function(obj, callback) {
  var username = obj[key];
  if (username) {
    var selectSql = sql1 + '\'' + username + '\'' + sql2; // 拼接查询语句
    connection.query(selectSql, function(err, rows) {
      if (err) {
        callback(err);
      } else {
        // 如果rows对象为空，则表示当前查询为空即email未激活
        if (!rows || !rows[0]) {
          counter++;
          console.log(''+counter, username);
        }
        callback();
      }
    });
  } else {
    callback();
  }
}, function(err) {
  // 打印错误，关闭数据库连接
  if (err) {
    console.log('Error: ', JSON.stringify(err));    
  }
  connection.end(); 
});
{% endcodeblock %}

关键代码讲解：
<ul>
<li>第7~10行：先获取workbook的第一个sheetName，然后通过sheetName获取到worksheet，然后通过xlsx的utils.sheet_to_json方法将worksheet转换成JSON对象数组</li>
<li>第13~19行：将数据库的连接配置传入mysql提供的createConnection方法，创建数据库连接</li>
<li>第26~44行：通过async.eachSeries方法遍历用户JSON数组，通过mysql连接提供的query方法异步查询数据库</li>
<li>第74~80行：在async.eachSeries遍历结束后，打印错误信息并关闭MySQL连接</li>
</ul>

### 运行效果
  <img src="{{ root_url }}/images/custom/20150113/result.png" />

关于xlsx，mysql以及async的详细用法，请到npmjs网站上去搜索查看：[npmjs](https://www.npmjs.com/)

以上。