---
title: "电子邮件同步到twitter/新浪/腾讯微博"
date: "2011-04-12"
slug: "2011-04-12-email-weibo"
image: "berry.jpg"
categories: 
  - "it互联网"
tags: 
  - "电子邮件"
  - "twitter"
---

一直以来Blackberry很少受到国内新浪、腾讯的重视，Blackberry上的QQ以前一度只有第三方修改版，而新浪微博的Blackberry客户端据说还是黑莓中国分公司主动联系新浪开发的。

但是用过黑莓新浪客户端(下图左)的应该都有感触，这玩意，简直就是粗制滥造，用户体验糟糕得稀里哗啦的。用这种客户端，还不如黑莓自带浏览器省心省力(下图右)。

各大微博在创建之初就建立了各自的短/彩信更新微博方式，但长期以来，罕有人用。至于今天要提到的Email发布，则是更加没人问津。但既然存在这么种可能，也是可以为之一试的。

根据个人经验，使用Email发布到微博有以下几个优点：

1，免费；不需要短信/彩信费，按照一天三条的速度，一个月好歹可以省下10块钱嘛...

2，审查较为宽松，没有关键词过滤。

3，可以在解决这个问题的同时引发一些新的兴趣。

 

下图就是我使用邮件更新到疼讯/新浪微博的过程，直接看图不清楚的话，我再简单解释下，估计就很清晰了。

首先，我们在Wordpress.com注册一个帐号，然后在后台“设置—撰写”中开启Email发布功能，指定一个自己新注册的，不会被人知道的邮箱作中转。

\[注1\]：通过Blackberry/或者其他手机的电子邮件发送功能，将需要更新的信息发送到这个电邮地址，然后就能自动更新你的Wordpress.com博客。

\[注2\]：如果是wordpress.org的用户，关于如何配置电子邮件发布功能，可以观阅我[这篇]文章，或者不倒翁的[这篇]文章。

其次，通过Wordpress的插件[wp-follow5](http://wordpress.org/extend/plugins/wp-follow5/)或者[wp-connect](http://wordpress.org/extend/plugins/wp-connect/) 等wordpress插件，自动将发布的文章更新到微博，我这里之所以选择wp-follow5再作一次中转，是因为follow5的转发功能实在是过于强大，几乎国内/国外主流的微博乃至facebook/人人网都可以同步，而wp-connect这类插件如果要实现这么强大的转发功能，势必对服务器造成一定压力。

然后，我们在follow5登录，并设置[各种同步]就可以了。

实际测试中，邮件同步是有一定延迟的，这个延迟主要发生在邮件到wordpress的同步过程中，（wordpress.org是根据插件的设置时间而异，wordpress.com我印象中是在10分钟之内)。由于我不特别重视这个，所以设置了1个小时更新一次，对我来说也够了。

另外，我要解释的是关于选择这个同步的首要原因是因为我没有太多时间同时去更新自己的notepad.tk，以及各种微博，所以尽量选择一种最省的方案吧，因为所有内容都是先发布在wordpress的，理论上任何言论都会有存档，不用去理会在新浪写了半天微博，竟然提示无法发送这类杯具。

最后我还要提到的是，我这种方式仅仅是一种同步的思路，用邮件同步到各大微博还有很多方案的。例如说[这种]用Email更新到Blogger(和wordpress.com一样)，然后用twitterfeed导入Blogger链接再同步到Twitter，或者使用一个posterous.com上的专业Email同步Twitter的服务。

仍旧给自己的微博卖个广告：Twitter @Rpwi

最终效果：

[Wordpress平台]

[腾讯微博]



发布前突然想到一个严重的问题：Wordpress到微博时，只会同步文章标题和链接，所以最好是单独创建一个P2主题的Wordpress站点进行中转操作，貌似p2主题默认截断40个汉字，可以将其改到140。

关于同步字数问题，在p2主题或者gtd的主题，修改functions.php中`function prologue\_title\_from\_content( $content )`下`max\_len=40`为`max\_len=140`即可完美解决。