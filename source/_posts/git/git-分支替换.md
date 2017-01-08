---
title: git 分支替换
date: 2016-06-02 13:26:07
tags:
- hexo
- git
- jekyll
categories: git
---

## 问题
在写github写博客时，有两个很好的工具，一个是hexo，一个是jekyll。为了方便自己学习，使用两个分支分管hexo与jekyll。但代码要推到github的master分支。本来考虑在本地替换分支再推到github的master分支。但。。。
## 方法
将hexo分支推到远程的master分支。
``` bash
$ git push origin hexo:master -f
```
可以解决，而且，本地的master也没有做修改。如果要将本地master也修改。
``` bash
git checkout master
git reset --hard develop  //先将本地的master分支重置成develop
git push origin master --force //再推送到远程仓库
```
<!-- more -->
## 最后
最后，发现hexo不是把本地的博客文件全推到github上，而是有上deploy命名进行了管理。白折腾了。hexo与jekyll的区别在于，hexo是在本地写好博客，然后“编译”上传到github，而jekyll不是，github直接支持了，jekyll的代码“编译”成了静态网页。hexo自己“编译”静态页面，jekyll是github编的。
