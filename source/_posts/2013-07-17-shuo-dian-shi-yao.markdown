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

##补记
配置站点的时候，我由于有第一次实践的经验，将站点根目录下的配置文件_config.yml进行了修改，比如博客title、subtitle什么的。更有用的是修改了3rd Party Settings下的那些插件配置。

具体来说就是用#注释掉了大部分的插件调用，像twitter、facebook、Pinboard这些，一来我也不用它们，二来咱中国用户被墙了，不但访问不了这些服务，还被拖慢了博文的加载速度。所以注释掉它们是一个优化页面的小技巧。

#功能更新：disqus评论插件
##起源
心痒痒，觉得博客没有评论模块不完整，又看到大家的Octopress博客都带上了美观实用的disqus插件，自然我也得弄一个出来。
##参考
- 心静茹水：给octopress添加Disqus评论功能

<http://seagg.github.io/blog/2012/09/03/config-comment-on-octopress/>

这篇博文很清楚地介绍了添加disqus的步骤。
##历程
###注册disqus账号
按照上面那篇博文的步骤，在disqus官网进行注册。我把注册页面的Register your site for free和Primary Moderator两部分都填了。要注意的地方是，它会给你生成（如果没有，自己填也行，推荐用英文字母）一个叫`Site Shortname`的名称，这个得记住，我的是itechblue。接着点继续，它就转到一个页面教你怎么将disqus集成到自己的网站去。

`可是Octopress已经集成了disqus...优越感油然而生=p`

最后去注册时填的邮箱查看激活邮件，然后点激活就算好了。
###修改站点配置
去到站点根目录下，打开配置文件_config.yml，找到3rd Party Settings下的disqus配置，将注册时得到的Site Shortname赋给disqus_short_name，看起来是这样的：

{% codeblock %}
# Disqus Comments
disqus_short_name: itechblue
disqus_show_comment_count: false
{% endcodeblock %}

细心的话，能留意到我们新建的博文(source/_posts下的markdown文件)的头部写有配置项，其中就有自动生成的comments: true，也就是可评论。

反过来说，将其设为false，就不可评论了。我的hello world那篇博文就是如此。
###发布
预览    `rake preview`

生成    `rake generate`

发布    `rake deploy`

同步代码 `git add .` `git commit -m 'xxx'` `git push orgin source`
###尝试
disqus评论模块这就出来了，还真方便。赶紧自己抢个沙发。在自己的disqus账号页面也能看到评论记录：

{% img center /images/first_comment.png 290 100 'first comment' 'first comment' %}

>为了显示图片，我还特地查了资料：
[How to insert image into octopress framework?](http://stackoverflow.com/questions/13486512/how-to-insert-image-into-octopress-framework)