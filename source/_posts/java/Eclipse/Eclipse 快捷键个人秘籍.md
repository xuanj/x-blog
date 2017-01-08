---
title: Eclipse 快捷键个人秘籍
date: 2016-08-20 01:22:00
categories: Eclipse
tags:
- java 
- Eclipse
---

> 经常被同学、同事、家人、亲戚、朋友问到，我怎么没有鼠标。因为，我买不起。

# 按键
本人使用mac，windows自觉对应。

| 按键相貌         | 按键名          | 说明  |
|:-------------:|:-------------:|:-----:|
|⌃ |Control/Ctrl|控制键，最次的按键，vim里最常用，小指要残 |
|⌥ |Option/Alt |选择键,次选前缀，大拇指勉强方便可以按到。|
|⇧ |Shift |上档键，小指可以方便按到，但被输入占用|
|⌘ |Command | 大拇指方便按到，而且大拇指力大，前缀使用|
# 默认快捷键
这些是值得记录一下的快捷键。
⌃Q：上一次编辑位置
⌘-/=：代码的收缩与扩展，可惜，for，while等不能用，vs却能用
⌃.：完成单词，有两个快捷键，别一个自定义是⌘4


# 自定义快捷键
这些是自己设置的快捷键。每个人java程序员都应该有自己的一套自定义快捷键。下面每个分类都有不同的前缀，如同vim里的mapleader一样。
前缀设置，与mapleader一样，快捷键分两次按下，第一按下为前缀。
⌘P，先将这个的打印快捷删除，没必要在Eclipse打印。
<!-- more -->
## 视图切换
不同透视图之间快速切换，添加快捷键后，可以隐藏掉没用的toolbar。后续会添加自定义的透视图。
⌘F8可以在Toolbar上的透视图之间切换。
透视图前缀：⌘P
J：Java
D：调试
B：代码浏览
G：Git
T：Team
O：Toad 

下面是Show in的：
R：Remote System远程服务上的文件。
E：Package Explorer 代码最佳，代码文件不用Link到Package上，Link显示业余。
H：历史
C：控制台
S：Server服务器

## 调试
更多参考之前的文章 [《Eclipse Java调试技巧》](http://xuanjian.site/java/Eclipse/Eclipse%20Java调试技巧/)。
一此没有前缀的快捷键：
⇧⌘D：在Server里以Debug启动服务
⌥⌘P：部署到服务器上

调试前缀：⌘;
V: Show in (Variables)
B: Show in (Breakpoints)
E: Show in (Expressions)
D: Drop to Frame
C: Remove ALL Breakpoints 删除所有断点
R: 重启开始调试
S: 关闭程序，中止调试
L: Run To Line 运行到光标行

## java编辑
编辑要快，这里无前缀快捷键。
⇧Space：代码补全，默认那个不方便。
⌘R：重构

java编辑前缀：⌘J
J：新建java类
I：新建接口
R：此类被哪些类引用 Search for references
G：生成Getter和Setter，Bean常用

## 其他
没前缀的快捷键：
⌥B 添加Bookmarks

一些未分类的快捷键，前缀：⌘'
V：Toggles Vrapper ：vim的启用与关闭
[：垂直分屏
-：水平分屏
G：Go Into 在Explorer中深目录，更专注
H：Back 在Explorer中退后上目录
L：Forward 在Explorer中前进到之前目录
J：Up 在Explorer中上层目录
明白人一看就知道，这是参数了vim里的按键设置。

# 快捷键保存文件位置
``` bash
工作目录/.plugins/org.eclipse.core.runtime/.settings/org.eclipse.ui.workbench.prefs
```
以org.eclipse.ui.commands开头的那行就是自定义的快捷键信息，如果没有设置过自定义快捷键，那么就没有这行。
# 自己定义的commands

最近一次更新定义文件的时间：2016-08-20
{% codeblock lang:xml %}
org.eclipse.ui.commands=<?xml version\="1.0" encoding\="UTF-8"?>\n<org.eclipse.ui.commands>\n<keyBinding commandId\="org.eclipse.ui.newWizard" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+J I">\n<parameter id\="newWizardId" value\="org.eclipse.jdt.ui.wizards.NewInterfaceCreationWizard"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.perspectives.showPerspective" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P J">\n<parameter id\="org.eclipse.ui.perspectives.showPerspective.perspectiveId" value\="org.eclipse.jdt.ui.JavaPerspective"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.edit.text.hippieCompletion" contextId\="org.eclipse.ui.textEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+4"/>\n<keyBinding commandId\="org.eclipse.ui.window.splitEditor" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; -">\n<parameter id\="Splitter.isHorizontal" value\="true"/>\n</keyBinding>\n<keyBinding contextId\="org.eclipse.jdt.ui.breadcrumbEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+COMMAND+B"/>\n<keyBinding commandId\="org.eclipse.debug.ui.commands.DropToFrame" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; D"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.forward" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; L"/>\n<keyBinding commandId\="org.eclipse.debug.ui.commands.RemoveAllBreakpoints" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; C"/>\n<keyBinding contextId\="org.eclipse.debug.ui.debugging" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+R"/>\n<keyBinding commandId\="org.eclipse.debug.ui.commands.TerminateAndRelaunch" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; R"/>\n<keyBinding commandId\="org.eclipse.jdt.ui.edit.text.java.rename.element" contextId\="org.eclipse.jdt.ui.javaEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+R"/>\n<keyBinding commandId\="org.eclipse.egit.ui.RepositoriesLinkWithSelection" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+SHIFT+L CR"/>\n<keyBinding commandId\="org.eclipse.ui.perspectives.showPerspective" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P G">\n<parameter id\="org.eclipse.ui.perspectives.showPerspective.perspectiveId" value\="org.eclipse.egit.ui.GitRepositoryExploring"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P H">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.team.ui.GenericHistoryView"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.jdt.ui.edit.text.java.search.references.in.project" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+J R"/>\n<keyBinding contextId\="org.eclipse.jdt.ui.javaEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+COMMAND+B"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P C">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.ui.console.ConsoleView"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.edit.text.contentAssist.proposals" contextId\="org.eclipse.ui.contexts.dialogAndWindow" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="SHIFT+SPACE"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; E">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.debug.ui.ExpressionView"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.perspectives.showPerspective" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P B">\n<parameter id\="org.eclipse.ui.perspectives.showPerspective.perspectiveId" value\="org.eclipse.jdt.ui.JavaBrowsingPerspective"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P E">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.jdt.ui.PackageExplorer"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.perspectives.showPerspective" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P T">\n<parameter id\="org.eclipse.ui.perspectives.showPerspective.perspectiveId" value\="org.eclipse.team.ui.TeamSynchronizingPerspective"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; V">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.debug.ui.VariableView"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.newWizard" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+J C">\n<parameter id\="newWizardId" value\="org.eclipse.jdt.ui.wizards.NewClassCreationWizard"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.perspectives.showPerspective" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P D">\n<parameter id\="org.eclipse.ui.perspectives.showPerspective.perspectiveId" value\="org.eclipse.debug.ui.DebugPerspective"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.edit.text.folding.expand" contextId\="org.eclipse.ui.textEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+\="/>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P R">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.rse.ui.view.systemView"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.edit.text.folding.collapse" contextId\="org.eclipse.ui.textEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+-"/>\n<keyBinding commandId\="net.sourceforge.vrapper.eclipse.commands.toggle" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; V"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.up" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; J"/>\n<keyBinding commandId\="org.eclipse.ui.project.buildProject" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+B"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.goInto" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; G"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.back" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; H"/>\n<keyBinding contextId\="org.eclipse.ui.serverViewScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+COMMAND+D"/>\n<keyBinding commandId\="org.eclipse.debug.ui.commands.Terminate" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; S"/>\n<keyBinding contextId\="com.spket.ui.textEditScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+]"/>\n<keyBinding commandId\="org.eclipse.wst.server.debug" contextId\="org.eclipse.ui.serverViewScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+SHIFT+D"/>\n<keyBinding contextId\="org.eclipse.ui.contexts.dialogAndWindow" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+/"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P S">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.wst.server.ui.ServersView"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.jdt.ui.edit.text.java.create.getter.setter" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+J G"/>\n<keyBinding commandId\="org.eclipse.ui.edit.addBookmark" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+B"/>\n<keyBinding commandId\="org.eclipse.debug.ui.commands.RunToLine" contextId\="org.eclipse.debug.ui.debugging" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; L"/>\n<keyBinding contextId\="org.eclipse.ui.textEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+NUMPAD_SUBTRACT"/>\n<keyBinding contextId\="org.eclipse.ui.textEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+NUMPAD_ADD"/>\n<keyBinding contextId\="org.eclipse.ui.textEditorScope" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+COMMAND+/"/>\n<keyBinding commandId\="org.eclipse.ui.navigate.showIn" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+; B">\n<parameter id\="org.eclipse.ui.navigate.showIn.targetId" value\="org.eclipse.debug.ui.BreakpointView"/>\n</keyBinding>\n<keyBinding commandId\="org.tigris.subversion.subclipse.ui.update" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+U"/>\n<keyBinding commandId\="org.eclipse.ui.perspectives.showPerspective" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+P O">\n<parameter id\="org.eclipse.ui.perspectives.showPerspective.perspectiveId" value\="com.dell.toadext.ToadextPerspective"/>\n</keyBinding>\n<keyBinding commandId\="org.eclipse.ui.window.splitEditor" contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+&apos; [">\n<parameter id\="Splitter.isHorizontal" value\="false"/>\n</keyBinding>\n<keyBinding contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="ALT+COMMAND+R"/>\n<keyBinding contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+SHIFT+-"/>\n<keyBinding contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+SHIFT+["/>\n<keyBinding contextId\="org.eclipse.ui.contexts.window" keyConfigurationId\="org.eclipse.ui.defaultAcceleratorConfiguration" keySequence\="COMMAND+B"/>\n</org.eclipse.ui.commands>
{% endcodeblock %}