---
title: "为何1000M光纤宽带，有时候测速只有300M"
date: "2020-01-19"
slug: "why-1000m-fiber-broadband-sometimes-the-speed-is-only-300m"
categories: 
  - "IT互联网"
tags: 
  - "光纤"
  - "网件"
  - "路由器"
image: "images/2023-04-15-155723-1.png"
---

写这个问题，主要是因为在百度上搜索了各种信息，基本都是千篇一律洗稿内容，鲜有讲清这个问题的文章，大多数都是瞎扯淡，有些讨论下边，还各种对提问者讥讽、人身攻击，丝毫没有解决问题的思路，由于个人刚好遇到这个问题，现在这里写一下解决办法。

## 一、为何1000M光纤宽带，测速只有300M？

可能原因：**路由器WAN TO LAN速率限制；路由器未开启硬件加速。**

1. 前提确认：网络已升级1000M光纤，光猫支持千兆输出，路由器WAN、LAN口均支持1000M千兆速率。

2. 到http://Smallnetbuilder.com查询路由器WAN TO LAN速率。

  > 网件 netgear r7000 WAN TO LAN速率 ：931Mbps
  > 网件 netgear r6300v2 WAN TO LAN速率 ：806Mbps
  > 华硕 ASUS ac68u WAN TO LAN速率: 754.5Mbps
  > TP-LINK TGR1900 WAN TO LAN速率: 631Mbps
  > 网件 netgear r6100 WAN TO LAN速率:93.1Mbps

  其他杂牌路由器，有可能其自身硬件能力不行，WAN TO LAN速率本身就低，wan口接入1000M，LAN口输出300M也就不奇怪了。

3. 路由器设置中是否开启NAT硬件加速，是否开启巨型帧，是否开启生成树协议。

实测，R6300V2在未开启NAT硬件加速情况下，WAN口1000M输入，LAN口只能输出300M。

在开启NAT硬件加速、巨型帧、生成树协议的情况下，WAN口1000M输入，LAN口可输出800M。

![](images/屏幕截图-2023-04-15-155318.png)

## 二、为何1000M光纤宽带，测速只有800M或者920M？

例如，在nga上有人提问“电信千兆宽带测速只有800~900M”，下边很多回答基本都没讲到点子上，核心问题在于主流1000M wifi6路由器WAN TO LAN最高速率也就920Mbps左右。在上边网站，可查询相关测试结果。

![](images/屏幕截图-2023-04-15-154615-932x1024.png)
