---
title: "DNS解析是干嘛的"
date: "2010-09-16"
slug: "2010-09-16-dns"
image: "pexels-photo-1148820.webp"
categories: 
  - "it互联网"
tags: 
  - "dns解析"
---

一直都没怎么注意DNS解析的设置（主要指解析速度方面），最开始使用的是域名注册商自己的NS服务器，但感觉制约太多，所以很长一段时间都在使用namecheap的免费ns解析服务，即使之后一直在godaddy注册也还是保持一贯作风，注册域名后第一件事就是把ns改为freedns.namecheap.com之类。

NS的基础作用就是告诉终端用户，你输入的网址将被指向到IP，这里涉及到的是互联网最简单的IP与域名关联，不再赘述。

按照这方面理解，可以将日常访问网站的过程解析为如下步骤：

1，在浏览器中输入网址http://ifosu.com；

2，本地的域名服务器202.192.168.38（校园网内部dns服务器）收到上面需要访问网站的请求后查询本地服务器的缓存；

3，如果第二步服务器缓存没有记录，则这台服务器会将第一步的请求向某台国际根域名服务器发出请求，全球的任何一台根服务器都会记录ifosu.com的真实NS服务器dns.dnspod.com，从而其将前述请求转发到dns.dnspod.com；

4，当请求到达dns.dnspod.com服务器，这台服务器将会查询到本地的A记录 ifosu.com  208.89.212.251，从而使访问ifosu.com 的请求返回到208.89.212.251服务器；

5，208.89.212.251服务器收到请求后，向我电脑传输网页数据，并由我本地浏览器解析出来网页。

由上述过程可见，一个网站访问速度的快慢与ns服务器还是有很大关系的，如果域名的ns服务器距本地太远，很容易拖累网站访问速度；本网站实测在使用namecheap的ns服务器期间，长期在一秒以上，3-5秒也不意外，如今更换了dnspod，前期时间应该是可以忽略不计了。

之所以当时会选择namecheap，主要是出于对国内dns环境的不理解，经常接触到一些批判国内dns安全环境十分恶劣的文章，耳濡目染中产生了极大的不信任，如今虽然依旧如此，但出于对网站访问速度的考虑，还是隐忍不发了。

Dnspod包括以下6类解析：A、Cname、X、AAAA、TXT、NS

Namecheap除了上述6类还有：URL 转发、URL 301重定向、URL 隐藏转发；

Dnspod对于TTL有限制，免费服务不得小于600秒，而Namecheap对于TTL无限制；

此外还有其他细节区别，例如Dnspod提供中国特色的多线解析，而Namecheap也提供动态解析和SRV记录等等。

