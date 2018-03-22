---
title: git 打包
date: 2018-03-22 11:21:14
tags: git 
---

> “取个代码给我，不要带有版本信息”
> “啊~哦~”

--- 
git有提供打包命令：git archive。

# 导出最新代码
```bash
git archive -o last.zip HEAD
```
# 导出指定版本
```bash
git archive -o some.zip 9d32107
```
# 导出指定文件夹
```bash
git archive -o some.zip HEAD:source
```
