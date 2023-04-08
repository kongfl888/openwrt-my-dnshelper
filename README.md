# [mY]DNS助手 for OPENWRT

## 简介

[my-dnshelper](https://github.com/kongfl888/openwrt-my-dnshelper)

这是我个人编写的，轻量级的路由器插件/app，含WebUI。辅助用户更好地设置路由器DNS服务器。目的在于以最小的再安装来达到优化家庭网络，完成DNS净化效果。

Hi, friends. You can use it to set your dns server of your route. It's very small, but helpful for users who limited by devices. Of course, it's written by me.

## 许可

基于[GPLv2](https://github.com/kongfl888/openwrt-my-dnshelper/LICENSE) ，这意味着任何人都可以对其作出修改，但这也是一个污染协议，意味着你必须对其再开源。请保留并附带这份协议。

你可以免费使用它，而不是通过商业的途径。

LICENSE. 

You should know what GPLv2 is. Yep, that GPL.

It's Free for everyone.

## 功能

- 域名过滤（注意：这不是去广告。但可以避免被某些欺诈等不良信息侵害，和保护儿童身心健康）

- DNS防污染 （做法当然是更换相对纯净的DNS商，简单易懂的界面。支持加密DoH（DNS Over Https），但这需要https-dns-proxy的支持，同样也是一个轻量级的软件，由OPENWRT推荐的功能搭配）

- 支持规则订阅，过滤必然的需求，总有好人会分享他们的成果，就如同本项目一样

- 支持用户自定义规则，自定义是需要的

总结，就像是搭建一个正常的DNS服务器，做点正常的DNS要做的内容。是不是很奇怪它为什么能做到，因为它本身就依赖于路由器系统openwrt自身的dnsmasq，很熟悉对吧。

不需要很强大的功能，只需要把openwrt的dnsmasq用好。

回归纯粹。

这应该是家庭用户需要的吧，因为我便是有了这么一个需求，才写了这个。不需要安什么，让它们都走开。

当然了，要用得好，固件编译的时候还是得dnsmasq-full，含ipset，民间自产的固件一般都是这个吧，也就不算额外，相关的依赖更是早就在出炉的时候就待在系统里了。不是full的，部分的功能不会有作用。

In a word, this is a HELPER tool for the DNS server that comes with the router.

So, you of course know what dns is. Helper, it can not do all the things, but it can do something to help you.

Filter, customize dns server... somethings like that.

dnsmasq-full is recommended.

You also may need https-dns-proxy which mentioned by openwrt org, if you need DoH. Yes, all small. Thank them.

## 依赖

Depends

``dnsmasq-full``

``curl or wget-ssl`` （用于规则更新 Update Rules，推荐curl recommended）

``https-dns-proxy`` （可选/Optional, DoH的支持组件/For DoH）

安装https-dns-proxy直接运行

```
opkg update
opkg install https-dns-proxy
```
如果你的固件已经安装了curl，那大概是20kb左右（本体）。
在编译固件的时候也可以直接选择，又或者使用这个[openwrt-https-dns-proxy](https://github.com/kongfl888/openwrt-https-dns-proxy)
https-dns-proxy 不是必须的，除非你想使用这里的DoH。

本包不会做依赖限制，所以这些需要你自己选上或者安装，一般都有。

## 支持的自定义规则

DNS助手支持以下规则

It support rules.

```
@@||abc.xyz^              not block this domain

||abc.xyz^                block this domain

127.0.0.1 abc.xyz         hosts

server=/abc.xyz/1.1.1.1   use dns 1.1.1.1 for abc.xyz
```

支持AdguardHome/Dnsmasq/Hosts/Domain类规则的在线订阅

Support AdguardHome/Dnsmasq/Hosts/Domain updated online.

## 冲突

我也不知道，除了DoH属于盖楼，其余就是dnsmasq的应用方式。会不会冲突，你需要考虑的只是dnsmasq的情况。

比如：过滤的。当然，单靠域名也就是DNS是不足的，所以还得加个GG插件，感谢某byby，我就一直在搭配着用（就自定义规则，其他都没有，改天我再放一个[精简过的自用版](https://github.com/kongfl888/luci-app-adbyby-plus-lite/releases)）。
附：不要指望一个路由器能做到浏览器那种程度。

Conflict.

I don't know yet. Please help yourself. But all you need to consider is dnsmasq.

## 支持系统

新版的吧，18的WebUI我也不想做支持了。旧时的也不知道什么时候会被抛弃，免得到时候还得移植一遍。

System.

openwrt 19+

## 致谢

第三方规则的分享者以及收集者（国内anti项目、adguard、yhosts、Cats-Team等）

(K)
