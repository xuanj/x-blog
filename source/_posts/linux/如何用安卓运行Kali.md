---
title: 如何用安卓运行Kali
date: 2016-06-03 12:22:00
tags:
- linux
- kali
- ide
---

> 对于想学习linux，python，shell，vi等的同鞋，请收下。
对于想用kali学习安全与渗透方法的同鞋…… 确实可以省去虚拟机的麻烦事。
此文安装的发行版本是Kali sana,linuxdeploy支持很多linux的发行版本。
直接用手机当主机也不是不可能的。现在手机，动不动就是8核的。

# 为什么想用在手机上运行linux。
0、手机成为极客工具。
1、手机方便，linuxer必备。
2、码农，随时随地打开手机就可以工作。
<!-- more -->

# 原理
一个字：虚拟机。

# 安装
0、[busybox](https://github.com/meefik/busybox) 
1、[linuxdeploy](https://github.com/meefik/linuxdeploy)
2、[terminal](https://github.com/jackpal/Android-Terminal-Emulator)

这些都可以在github上找到，是开源的项目。请自觉到releases那里下载最新版本。
3、JuiceSSH （选装）
这个ssh链接工具，一个非常不错的终端。因为，它可以提供一个特殊字符的直接输入，这样在没有物理键盘的情况下非常好用。如果接个蓝牙键盘，那就是别当别论了。

在安卓上运行linux，用到的是chroot。(这不就是docker上用到虚拟技术)看下项目READM.md的说明：
>Applications of the new system are run in a chroot environment and working together with the Android platform.

运行在chroot环境，和安卓一起工作的。linuxdeploy运行起来后top一下就可以看到安卓的进程了。
机器要先root，并且先安装busybox，才可以安装linuxdeploy。安装过程就不说了，有问题可以到github上的Issuues上面找找。如果安装这三个软件也成问题，那你就不会看到这渣文。

# 配置
linuxdepoy是用联网进行安装linux，所以，网速很让人抓狂。可以将源设置成科大的，速度相当不错。修改镜像的地址：http://202.141.160.110/kali/
{% img class /images/如何用安卓手机做开发_1.jpg 240 Mirror URL  %}
其他的参数自己看办。
后期我会将自己的img上传到百度分享出来，因为联网安装失败可能性大。下载img文件，然后替换掉原来的img就可以启动。这样直接安装好kali常用的软件，方便大家使用。

# 如何在终端行里启动
为了解决三星手机无法在ssh下用root用户登录，没有root就无法apt-get，但，可以直接在终端里直接用root权限运行linuxdeploy。
0、打开命令行
1、su 获取root权限
2、转到linuxdeploy的bin目录下
3、启动
``` bash
su
cd /data/data/ru.meefik.linuxdeploy/files/bin
./linuxdeploy shell
```
{% img class /images/如何用安卓手机做开发_2.jpg 240 Mirror URL  %}

现在，手上有了自己的Kali，随便折腾吧！
{% img class /images/如何用安卓手机做开发_3.jpg 240 Mirror URL  %}
