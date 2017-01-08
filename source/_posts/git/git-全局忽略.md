---
title: git-全局忽略
date: 2016-06-04 22:05:48
tags: 
- git
categories: git
---

> Mac 为每个目录生成.DS_Store;Eclipse 为项目生成.classpath等。
总会有些文件，你总想忽略。

解决文件：
# 一、添加要忽略的文件的文件 ~/.gitignore_global

<!-- more -->

``` bash
#.gitignore_global
# 要忽略的系统文件
.DS_Store
.DS_Store?
*.swp
._*
.Spotlight-V100
.Trashes
Icon?
ehthumbs.db
Thumbs.db
# 想忽略的包文件
*.7z
*.dmg
*.gz
*.iso
*.rar
*.tar
*.zip
# 其他
.settings/
```

# 二、添加git全局配置

``` bash
git config --global core.excludesfile ~/.gitignore_global
```

