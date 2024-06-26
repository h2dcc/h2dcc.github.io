---
title: "Wordpres及数据库使用SSH搬迁的简单方法"
date: "2010-07-27"
slug: "2010-07-27-wordpress-ssh-mysql"
image: "SSH.jpg"
categories: 
  - "it互联网"
tags: 
  - "putty"
  - "ssh"
  - "数据库迁移"
---

两年来，我的wp几乎是在搬迁中度过的，最近抓抓发起号召blogfans群员又合租了一个vps，Virpus提供的，7美刀/月，25G空间，100M带宽1600G流量；划为10份，由于正在优惠期，所以大概每人7.5美刀/年.

之前的主机是荷兰/葡萄牙，DA面板主机，仍然留下一个wp站点在那里，搬迁后的面板使用的是Kloxo，数据库均为MYSQL5.x(当然，4.x也是一样可以的)。


由于本人使用的校园网经常出现网络丢包，所以不得以所有操作均得在线进行，好在在线方式本来就是最简单便捷的。

**1.工具准备：**

可能需要的工具有Putty、cuteftp(如果习惯这种方式)；

putty是免费的ssh与talnet工具。

**下载地址：**[**putty**](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

进入原网站后台，选择备份整个网站（如果是英文，一般就是Creat backup项目），稍等片刻便可以进文件管理系统查看了。由于DA默认将备份的tar.gz文件保存在根目录下的backup文件夹，所以需要将其剪切或者复制到原网站的目录下，例如我将这个xxx.tar.gz剪切到了faxue.info/wordpress/uploads/下面，之所这样做的原因是能让这个xxx.tar.gz有一个理所当然的下载url.

**2.使用putty将网站备份下载到新主机**

打开putty,直接填写新主机的IP地址，然后选择“SSH”模式，点击“open”或者按回车就可以进入如DOS的操作界面了。

login as: admin（输入新主机用户名）

admin@208.89.212.251‘s password: abc123 （输入新主机密码，这里输入的时候，操作界面是不会显示的，输完密码直接回车）

显示如下内容则成功登录：

> login as: admin 
> admin@208.89.212.251's password:  
> Last login: Tue Jul 27 12:03:06 2010 from 61.142.209.146  
> \[admine@vip ~\]$

输入“ls”打开根目录，或者还可以使用“cd admin.tk”进入文件夹.

然后使用“wget” 命令将刚才备份的xxx,tar.gz下载到新主机：

> wget http://admin.tk/wordpress/uoloads/xxx.tar.gz

120MB的文件，压缩之后是40多MB，大概几秒钟就下载过来了吧…

下载完成后请删除原主机下的备份文件，因为移动后别人也可以下载啦，里面可保存着config.php之类的敏感信息

**3.解压**

使用文件管理器将xxx.tar.gz移动到某个文件夹解压，然后都是些复制剪切的工作，将新主机下的文件目录，按照原主机的目录模式编排好就完成大部分工作了。

**4.上传sql文件**

解压后找到备份的数据库文件，一般是backup文件夹内，认清数据库的名字，例如我的是faxue\_blog.sql，使用“mysql”命令上传数据库文件：

先在putty中使用“cd”命令进入faxue\_blog.sql文件所在的文件夹，

> cd faxue.info/domain/public\_html/backup

然后使用如下命令上传数据库：

> mysql -ufaxue –pabc123 faxue\_blog < faxue\_blog.sql

形式为：mysql -u用户名 -p密码 数据库名 < 需要上传数据库的文件名.sql

当然，这里的用户名、密码都是新数据库中的，建议提前在新主机的数据库管理中新建与原数据库相同名字的数据库，免得之后还得修改config.php。不过，如果你之前主机的用户名和新主机用户名不一样，之后还是得修改config.php。

**到这里，基本上问题也就解决，修改A记录即成功。**

下面的都是个人问题，不一定都能遇上：

1.我的原主机下绑定了N个子域名，安装了N个程序，wordpress、joomla、drupal、Gregarius等等，并且均为多个子网站使用同一数据库，只是不同前缀。使用上述方法，可以很方便的将之前网站所有资料搬迁过来。当然多个数据库的情况下，最后一步上传的工作就得做多次了。

2.原来主机下的数据库用户名与新主机数据库的用户名不同，之前的都是bensky\_，而新的均为faxue\_，所以所有网站、子网站都需要在上传之后将config程序中的数据库信息更新，不过数据库的表名前缀是不用换的，前后一致的。

3.遇上Vistapanel真是偶的一大杯具，因为vistapanel这种平台，只能解压而不能压缩还不支持fxp，使得我在byethost.com与xtreemhost.com上的网站无法备份过来(唯一的方法是将这两个主机上的所有文件全部下载到本地，然后再上传，没那个心情去弄.)，只能继续在那上面蹂躏了。
