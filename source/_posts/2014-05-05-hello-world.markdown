---
layout: post
title: "Hello World"
date: 2014-05-05 14:47:04 +0800
comments: false
categories: 其他
---
  
这是我博客（基于github与octopress）的第一篇文章。

摘抄部分Octopress指令：

<!-- more -->

Octopress 常用指令：

{% codeblock lang:sh %}
rake new_post["title"] 	# Generate a new post

rake generate   # Generates posts and pages into the public directory

rake watch      # Watches source/ and sass/ for changes and regenerates

rake preview    # Watches, and mounts a webserver at http://localhost:4000

rake deploy     # Deploy to github

git add .  &&   git commit -m 'your message'  &&  git push origin source
{% endcodeblock %}
