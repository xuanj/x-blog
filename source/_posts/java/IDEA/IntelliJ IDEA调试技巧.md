---
title: IntelliJ IDEA调试技巧
date: 2017-01-08 01:22:00
categories: IDEA
tags:
- java 
- IDEA
---

> IDEA 在调试过程中的一些小技巧，与Eclipse的调试做对比。不为分优劣长短，只是想看看，都有什么特点。 

# 快捷键
默认的常用快捷键：
x-blog新建分支。
为什么没有？
⌘5 debug 窗口
<!-- more -->

# 条件断点 
可以设置条件为true时才进入断点，也可以设置当值改变时进入断点。
{% img class /images/eclipse-debug1.png 650 条件断点   %}

# 异常断点
如果想在某种异常出现时，断点进入异常的代码行。
{% img class /images/eclipse-debug2.png 650 异常断点   %}

# Toggle Watchpoint
⇧⌘B 将类变量上添加观察点，当变量被访问或修改时进入。
{% img class /images/eclipse-debug3.png 650 Toggle Watchpoint   %}

# 修改变量值	
当调试时，希望将某变量在某值时的异常，可以直接在Variables里进行修改。修改了值之后记得⌘S保存值。不过，在修改数组时出现了错误。
{% img class /images/eclipse-debug4.png 650 修改变量值   %}

# Drop to Frame
跳转堆栈开始处。不服，不用再来一次。已经设置为前缀快捷加D。光标在哪里就从哪里重新开始。
{% img class /images/eclipse-debug5.png 650 Drop To Frame   %}

# 过滤
不是所有的代码都希望F5进入，比如sun或jdk的一些包，是的，我们不是来调试别人的代码的。当然，如果在研究一些源码，就不要这些过滤了。有时候，想将已经稳定的项目代码过滤下，也是好的。要结合快捷键⇧F5用。
{% img class /images/eclipse-debug6.png 650 过滤F5   %}

# Expressions视图
有些值，我们总想一直关注。 
{% img class /images/eclipse-debug7.png 650 Expressions   %}

# Display
这里可以直接写代码，然后选择代码运行。抛个异常什么的都可以。
{% img class /images/eclipse-debug9.png 650 Display   %}

# 逻辑结构
面对一些set和map，必须显示逻辑结构，不然，很难看。
{% img class /images/eclipse-debug8.png 650 逻辑结构   %}

# Step Into Selection
好货沉底，这招希望好用。
⌥⌘加上单击方法名就可以跳到方法上。非常好用，指哪打哪。如果一个函数太多参数，不用老是进入一些不想进入的方法里，避免过多F5、F7。结合⌘R会更好用。


