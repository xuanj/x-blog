---
title: iterm2如何快速ssh到远程服务器
date: 2016-06-10 22:05:48
tags: 
- iterm2
- ssh
categories: itmer2
---

> ssh登录到远程服务器，是经常的事儿，如何快速地ssh到远程服务器呢？你是怎么做的？

我是这样做的。直接快捷键⌃⌘s就可以打开一个远程服务器的窗口。
{% img class /images/iterm2-快速ssh到远程服务器_1.png 650 镇楼图 装13  %}
<!-- more -->

## 写个远程登录脚本

请自觉修改ipaddr，name，passwd的值。脚本内容如下：
``` bash
#!/usr/bin/expect -f
#Program:
#	This is ssh to remote server.
#History:
#2016/06/10 xuanjian First release
#不是bash，不可以用sentrisVPS.sh运行，可以在脚本目录用./sentrisVPS.sh远程
set timeout 10
set ipaddr "192.168.1.110"
set name "root"
set passwd "toor"
spawn ssh -l $name $ipaddr
send_user "Template Auto connect to remote server! \n"
expect {
	"yes/no" { send "yes\r"; exp_continue}
	"password:" { send "$passwd\r" }
	}
interact
```
## iterm2配置
添加一个远程登录的profile，设置iterm2快捷，并在打开时运行这个脚本。
{% img class /images/iterm2-快速ssh到远程服务器_2.png 650 iterm2配置图  %}

