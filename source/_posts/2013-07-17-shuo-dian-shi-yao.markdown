---
layout: post
title: "这个博客是怎么来的"
date: 2013-07-17 18:29
comments: true
categories: 
---

## 起源
机缘巧合之下，看到[阮一峰](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)说可以通过github搭建自己的博客，接着往下搜，又知道了[Octopress](http://octopress.org/)这个开源的博客框架。如其所说，“A blogging framework for hackers”,怎么也得自己折腾着搭一个才够酷啊！

## 参考
本人对web方面的东西特别没感觉，对github的使用是一知半解，对git命令更是云里雾里。然则明知山有虎偏向虎山行，我带着惭愧的心情和边折腾边学习的心态开始搜索资料。经过再三尝试，这个博客在主要参考了下面两个链接后初步建成：

- Octopress官方帮助文档

<http://octopress.org/help/>

- i沙漏的博文：使用Octopress + Github管理blog

<http://ued.taobao.com/blog/2012/07/getting-started-with-markdown/>

## 历程
###如何折腾
我首先潜心阅读Octopress的帮助文档，一步步从0开始，没什么就装什么，在自己也不知道怎么回事的情况下弄出了一个博客，而且还真能访问O__O"…但因为这时候我知其然不知其所以然，到最后竟然搞不懂怎么新建博文，只好先搁置。

这个阶段我的收获是：对整个搭建流程有了一个模糊的认识，也大概知道这过程中用的一些命令有何作用，而且安装好了所有用到的软件。

当今天我再次尝试时，是因为遇到了i沙漏的博文。相比官方文档，它更简练地展示了搭建的过程，所有关键步骤一个都不少，而且还有恰到好处的解说。有两样说明是我当时看官方文档没留意到的，一是执行如下语句后可以在本地访问<http://localhost:4000>进行预览:

{% codeblock %}
$ rake preview
{% endcodeblock %}

二是如何新建博文：

{% codeblock %}
$ rake new_post["new post name"]
{% endcodeblock %}

最终我按照博文的步骤一步步将博客搭建了起来。
###解决问题
这个过程中碰到一个问题就是github拒绝我的访问，我首先用如下语句检测是否有访问权限：

{% codeblock %}
$ ssh -T git@github.com
{% endcodeblock %}

发现还真没有，于是去到ssh目录下：

{% codeblock %}
$ cd ~/.ssh
$ ls
$ vim id_rsa.pub
{% endcodeblock %}

将id_rsa.pub的内容拷贝到github的设置页面-SSH Keys去添加，然后就可以访问了。

以上参考自[关于github的ssh, permission denied(publickey)](http://www.douban.com/note/201614252/)。
###开始编写
因为博文用markdown语言进行格式化，所以要写出美观大方的博客还得学习这种标记语言的使用。幸好网上有很多乐于分享的人们。

- 首先大概了解一下markdown

<http://ued.taobao.com/blog/2012/07/getting-started-with-markdown/>

- 接着，工欲善其事，必先利其器——Mou

<http://mouapp.com/>

Mou这个markdown编辑器一看就知道是个好东西。主页有图文并茂的介绍，软件界面让你能一边写一边看到效果。而且安装后打开的初始文件其实就是一份详尽的markdown语法实例，我果断先保存到了桌面。
这篇文章就是在预览模式下，我一边用Mou编写，一边刷新浏览器查看完成的。

##总结
首先按照官方文档去做，如果有问题，结合i沙漏的博文进行调整或者重试，这就差不多了。

官方文档和博文结合起来已经能确保博客的搭建成功，我就不做搬运工了。

##展望
目前搭建的博客仅仅简单地实现了编写博文、展示博文列表的功能。博客界面如何进行个性化定制、Octopress还提供了什么好功能，这都是我接下来要研究的地方。

当博文多起来的时候，起码能够归类吧！