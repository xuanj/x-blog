---
title: gitbook-安装与使用 
date: 2016-06-16 13:26:07
tags:
- gitbook
categories: gitbook 
---

> 习惯了markdown来记录学习，gitbook 用来做笔记再好不过。虽然名叫gitbook，可是与git没有半毛钱关系。gitbook就相似于hexo这种，只是一个用node.js开发出来的工具而已。

# 安装
gitbook是node.js整的，所以npm自然少不了。
``` bash
npm install -g gitbook-cli
```

# 新建一本书
新建一个目录/Users/Sword/git/gitbook，两个文件README.md（本书简介）、SUMMARY.md（这个文件重要，目录文件，gitbook根据这个文件生成目录与文件构造）。
<!-- more -->
## Summary 内容如下：
``` bash
# Summary

* [简介](README.md)
* [第一章](chapter1/README.md)
    * [第一节](chapter1/section1.md)
    * [第二节](chapter1/section2.md)
* [第二章](chapter2/README.md)
    * [第一节](chapter2/section1.md)
    * [第二节](chapter2/section2.md)
        * [第2.1节](chapter2/2.1/section2.md)
            * [第2.1.1节](chapter2/2.1/2.1.1/section2.md)
* [第三章](chapter3/README.md)
    * [第一节](chapter3/section1.md)
* [结束](end/README.md)
```

## 生成目录
``` bash
gitbook init
```
tree看下当前目录已经按Summary的构造生成了目录和文件。

# 启动
``` bash
gitbook serve
```
serve?一度怀疑是不是gitbook的作者这个启动命令不全。http://localhost:4000 访问看下自己的书。


