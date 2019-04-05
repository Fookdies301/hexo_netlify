---
title: proxifier注册码以及配合shadowsocks上网
tags:
  - proxifier注册码以及配合shadowsocks上网
categories:
  - proxifier
abbrlink: 6ae0d0de
date: 2019-01-15 23:04:11
---
# proxifier注册码以及配合shadowsocks上网
***
## 由于shadowsocks使用的是sockets5代理，一般情况下只有浏览器支持，可以实现科学上网。但很多用户希望自己的应用软件，像outlook或游戏之类的软件也实现科学上网。这就需要proxifier的配合。

---
<h2>
软件可以在官网下载，https://www.proxifier.com
或，http://www.onlinedown.net/soft/971579.htm
</h2>

***
# Proxifier基本简介

<h2>
　　Proxifier 是一款功能非常强大的socks5客户端，支持64位系统，支持Xp，Vista，Win7，支持socks4，socks5，http代理协议，支持TCP，UDP协议，可以指定端口，指定IP，指定程序等运行模式，兼容性非常好。
<h2>
　　Proxifier 解决了这些问题和所有限制，让您有机会不受任何限制使用你喜爱的软件。
<h2>
　　此外，它让你获得了额外的网络安全控制，创建代理隧道，并添加使用更多网络功能的权力。
</h2>

# Proxifier功能介绍
<h2>
　　1、Proxifier 绕过防火墙的限制。
<h2>
　　2、灵活的代理规则，对于主机名和应用程序名称可使用通配符。
<h2>
　　3、通过隐藏您的 IP 地址的获得安全隐私。
<h2>
　　4、查看当前网络活动的实时信息(连接,主机,时间,带宽使用等)。
<h2>
　　5、Proxifier 维护日志文件和流量转储。
<h2>
　　6、获得详细的网络错误报告。
</h2>

<h1>
Proxifier安装教程
</h1>

<h2>
1.在本站下载好Proxifier 数据包后，直接解压用鼠标双击打开进入安装向导，点击下一步

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/c48e6b5533de83dbc804f9ca9d4037e8.jpg)

<h2>
2.选择安装位置，默认路径为“C:Program Files (x86)Proxifier”
<h2>
3.在创建桌面快捷方式前面勾上，不然等软件安装好后在你的电脑桌面找不到Proxifier 软件哦
<h2>
4.等待安装完成即可
</h2>

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/4ab2ba58b0304fbc79f4ceb58b602728.jpg)

<h1>
Proxifier使用方法
</h1>
***

<h2>
一、设置代理
1、在安装Proxifier；
<h2>
2、在Proxifier的“配置文件”菜单上，单击“代理服务器”选项；
<h2>
3、在弹出的“代理服务器”对话框中，单击“添加”按钮；
<h2>
4、在弹出的“代理服务器”对话框中，输入代理服务器的IP地址和SOCKS端口，选中“SOCKS版本5”单选按钮，再单击“确定”按钮；

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/23634d8be3e0558167371778ca733175.jpg)

<h2>
5、在Proxifier “代理服务器”对话框中，单击“检查”按钮；
<h2>
6、在弹出“代理检查器”对话框中，将显示测试信息。
</h2>

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/0de3f4ab1078377f6a3a267e88006523.jpg)

<h1>
二、代理规则
<h1>
1、在Proxifier的“配置文件”菜单上，单击“代理规则”选项；
![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/064cf732d43cd8e621f4aa32336b2702.jpg)

</h1>

## 此软件为收费软件，这里提供两个注册码, 软件分为Standard Edition和Portable Edition版本，注册码不通用，注册用户名任意。


<h1>
``` js
L6Z8A-XY2J4-BTZ3P-ZZ7DF-A2Q9C（Portable Edition）
5EZ8G-C3WL5-B56YG-SCXM9-6QZAP（Standard Edition）
P427L-9Y552-5433E-8DSR3-58Z68（MAC）
```

---
或者：

用户名：www.3322.cc

注册码（秘钥）：（任选其一）

``` js
5EZ8G-C3WL5-B56YG-SCXM9-6QZAP
G3ZC7-7YGPY-FZD3A-FMNF9-ENTJB
YTZGN-FYT53-J253L-ZQZS4-YLBN9
```
</h1>
***

## 打开软件，首先配置代理服务器。
![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/6512bd43d9caa6e02c990b0a82652dca.png)

## 如下图，添加地址127.0.0.1，以及shadowsocks里配置的本地端口，默认为1080，选择socks version 5

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/c20ad4d76fe97759aa27a0c99bff6710.png)

## 配置好后，点击测试，如果显示下图的绿色文字，则表示配置正确。

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/c51ce410c124a10e0db5e4b97fc2af39.png)

## 接下来就要添加规则，来确定哪些软件是走代理的，哪些不用

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/aab3238922bcc25a6f606eb525ffdc56.png)

## 按如图所示的添加，这里有个default规则，如果default旁边的action里边选择的时proxy socks5…则本机所有软件都会走代理。一般default会选direct，然后把你需要走代理的软件选成proxy socks5…

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/9bf31c7ff062936a96d3c8bd1f8f2ff3.png)

## 最后在首页就能看到你各个软件的情况。

![](https://raw.githubusercontent.com/Fookdies301/tuc/master/03/c74d97b01eae257e44aa9d5bade97baf.png)
