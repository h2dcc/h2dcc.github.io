---
title: "用Wordpress打造你的网络记事本"
slug: "2011-01-07-wordpress-notepad"
image: "wordpress.jpg"
date: "2011-01-07"
categories: 
  - "it互联网"
tags: 
  - "wordpress"
---

Wordpress的强大之处在于你随便拿它做个神马站都不会觉得有太大压力，互联网上绝大多数应用都可以在wp平台下利用各种扩展实现目的，仅有的弱点可能就在于执行效率与二次开发的难度上面。

本人一度在记事本这个问题上纠结很久，面对evernote、麦库、Googlenotepad、Googlereader、Foxnotepad....等工具无所适从，到头来只得自己用wordpress折腾个算了。

我的要求其实很简单：**能够满足快速摘要的要求！无论是在PC还是在移动生活中。**

所幸的是，这个要求很容易就能够实现了。

下面是我实现这个要求的一些基本方法总结： 

## 平台搭建：

### 一，在已有的Wordpress博客中添加微博/记事本应用：

方法是无数的，我介绍的这种是很懒很懒的方法：

1,新建一个分类，命名为“微博”，记下这个分类的数字ID；

2,复制主题文件下的page.php改名为microblog.php，在文件最顶头加上下列说明

```
<?php /\*Template Name: Microblog\*/ ?>
```

3,在div class=“entry”之前插入

```
<?php $lastposts = get\_posts('numberposts=3&category=410'); foreach($lastposts as $post) : setup\_postdata($post); ?> <h2><a href="<?php the\_permalink(); ?>" title="<?php the\_title(); ?>"> <?php the\_title(); ?></a></h2> <div> <?php the\_date(); ?> <br /> <?php the\_content(); ?> <?php \_e('by'); ?> <?php  the\_author(); ?> <?php comments\_popup\_link ('No Comments &#187;', '1 Comment &#187;', '% Comments &#187;'); ?> <?php edit\_post\_link('Edit', ' &#124; ', ''); ?> </div> <?php endforeach; ?>
```

(注:第二行的“numberpost”代表页面显示记事条目多少、"category"后面的数字即第一步中的数字ID)

**函数扩充用法:**

参考1:[http://codex.wordpress.org/Function\_Reference/get\_posts](http://codex.wordpress.org/Function_Reference/get_posts)

参考2:[http://www.wordpress.la/codex-get\_posts.html](http://www.wordpress.la/codex-get_posts.html)

4,后台新建一个标题为“微博”的页面，内容空白，选择模板为"Microblog"，保存

5,将index.php以及archive.php的`<?php if(have\_posts()) : ?><?php while(have\_posts()) : the\_post();?>`前添加`<?php query\_posts($query\_string . '&cat=-410'); ?>`。数字410仍旧是上边的分类ID，目的是在首页及归档页面文章显示时排除微博，免得扰乱页面。

### 二，在新的wordpress博客中添加微博/记事本应用：

其实介绍了第一个方法也就没有必要再介绍如何在一个新的wordpress环境下折腾这个问题了。

但与兼容在一个既有平台不同的是，新的wordpress对于主题是没有限制的，所以完全不必像上面那样去折腾模板神马的，直接新建一个wordpress即可搞定。

1，新建一个wordpress站点；

2，下载安装p2、gtd或者其他你认为适合作为微博/记事本的主题；

## 快捷发布：

### 一，电子邮件发布：

wordpress的电子邮件发布无疑是最方便的更新方式之一。但长期以来wordpress.org平台在这方面做得并不够好，倒是.com平台更加人性化些，本人一度因为搞不定电子邮件发布功能而一气之下跑去wordpress.com瞎折腾了。

Wordpress的**电子邮件发布需要的一个插件是postie**，因为全是英文界面，可以看看不倒翁的这个教程：[http://www.spiaas.com/mood/650.html](http://www.spiaas.com/mood/650.html)

配置完电子邮件发布，剩下的事情就是手机方便的进行发布了。

黑莓平台推荐使用[Berrymail](http://berrymail.cn)服务，其他手机请自行搜索最便捷的电子邮件方案。

黑莓上发送电子邮件比短信更加快捷方便，这个是毫无疑问的，如果说手机上有比发短信更快捷的记事方式，我也无话可说了。

PC端的快捷电子邮件发布方式首推Firefox插件[Emailthis!](https://addons.mozilla.org/zh-CN/firefox/addon/3102/)或者[Emailyourself](https://addons.mozilla.org/zh-CN/firefox/addon/10300/)，此两者都能很便捷的在网络上对文字进行摘要并发送到指定的电子邮箱。

但实际上，由于电子邮件的安全性问题，所以很难说像麦库、GReader一样在浏览器设置一个按键直接把网络上的文字作摘要进行保存，但好在PC端我们还有比Emailthis更加快捷的方式。 

### 二，其他快捷发布方式：

什么Windows live writer就不说了，操作很慢，步骤也多，不符合要求，用wlw还不如word快，保存一个word的blog模板到快捷方式，粘贴就可以发布了，比wlw方便得多。

这里推荐的客户端依然是浏览器插件：[ScribeFire](https://addons.mozilla.org/zh-CN/firefox/addon/1730/ )

使用scribefire把网站信息配置好，每当遇到需要记下来的东西，直接鼠标右键“Scribefire”发布，再点确认发布即可。

其次推荐的是浏览器插件：[quickfox notes](https://addons.mozilla.org/zh-CN/firefox/addon/13572/)

配置好信息后，按右键选择需要保存的文字选择发送到“快捷笔记本”，再次右键点击内容即可启用电子邮件发布到博客。
