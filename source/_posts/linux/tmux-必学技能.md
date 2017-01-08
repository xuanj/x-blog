---
title: tmux-必学技能
date: 2016-06-09 22:05:48
tags: 
- tmux
- osx
- linux
categories: tmux
---

> tmux 对于经常终端占全屏的程序员或者运维人员而言，非常好用。值得拥有。

上一张图镇博。
{% img class /images/tmux-必学技能_1.png 650 镇楼图 装13  %}
<!-- more -->

## 初步体验
Mac 安装，当前版本2.1。
``` bash 
brew install tmux
```
注：C-b为Ctrl+b缩写。

1、启动
tmux
2、暂时断开连接，会话并没有关闭，活儿明天接着干
C-b d
3、重新打开之前的会话
tmux
4、关闭会话。
一个一个exit？不对！直接离开tmux会话
C-b & 

## 几个重要的概念
1、tmux 服务
tmux启动tmux服务，tmux服务可以包含多个session。
2、session 会话
一个会话可以包含多个窗口。
新建会话：
tmux new -s name
-s name 可以不要，这样新建的会话以数字依次命名。
C-b s 查看所有会话，选择一个Enter就可以在会话间切换。
3、window窗口
所见tmux窗口，是窗格的窗口。
C-b c
4、pane 窗格
只有一个窗格就是一个window窗口
C-b % 建新垂直窗格
C-b " 新建水平窗格
通过这个设置就可以创建多个空格啦。下这招要学会了。
C-b 空格
如果有多个窗格，上面这招可以使用内部布局，每次会换一个布局。

• 一个tmux命令执行后启动一个tmux服务
• 一个tmux服务可以拥有多个session，一个session可以看作是tmux管理下的伪终端的一个集合
• 一个session可能会有多个window与之关联，每个window都是一个伪终端，会占据整个屏幕
一个window可以被分割成多个pane

## 一个重要的文件.tmux
这个是配置文件，如同.vimrc一样。
``` bash
set-option -g status-keys vi
set-window-option -g mode-keys vi
bind-key h select-layout even-horizontal
bind-key v select-layout even-vertical
set -g mouse on #使用鼠标
set -g status off #关闭状态栏
bind D source-file ~/.tmux/mylayout
# bind a reload key
bind R source-file ~/.tmux.conf
```

这些设置就不一一讲解，只说一条:'bind D source-file ~/.tmux/mylayout'这个是一个自己定义的布局。

## 自定义布局
当你习惯了用tmux时，不用总是C-b %/" 来创建窗格。可以用一个文件设置空格，然后，将这个设置绑定到一个按键上即可。bind D就是绑定到了按键D上。
mylayout文件没有，所以先创建目录与文件，请自行创建。mylayout内容如下：
``` bash
selectp -t 0
splitw -v -p 50
selectp -t 0
splitw -h -p 50
```



