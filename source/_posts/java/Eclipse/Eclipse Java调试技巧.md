---
title: Eclipse Java调试技巧
date: 2016-08-19 01:22:00
categories: Eclipse
tags:
- java 
- Eclipse
---

> 开发、调试、测试、调试、改Bug、调试…… 开发状态经常在这几点一线间不断辗转。学习研究Eclipse的调试技巧，可以让开发事半功倍。 

# 快捷键
默认的常用快捷键：
⌘F11：调试运行、F8：下一断点、F7：跳出方法、F5跳出方法、F6下一行代码
⌘R：运行到光标所在行，不要一直F6
⇧⌘B：添加/删除断点 (如果在类变量上使用此快捷键，就是添加Toggle Watchpoint)
⇧⌘I：查看断点行的变量值，表达式的值也是可以查看的
⇧⌘D：也是查看断点行的变量值，但没有上面那个信息全
⌥⌘B：Skip All Breakpoints 跳过所有断点(Show In Breadcrumb “冲突”，所以将这个快捷删除掉)
⌘U：运行选择的代码，在Display视图里或者代码里直接用
⇧F5：是否启用过滤 Use Step Filters
自定义Debug中常用的快捷键，定义前缀：⌘;
V: Show in (Variables)
B: Show in (Breakpoints)
E: Show in (Expressions)
D: Drop to Frame
C: Remove ALL Breakpoints 删除所有断点
R: 重启开始调试
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


