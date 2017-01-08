---
title: neovim-在mac下安装
date: 2016-06-09 13:26:07
tags:
- vim
- neovim
categories: vim 
---

> 做为vim的未来版本，必须关注！

## brew 更新
``` bash
brew update
```
## brew 安装neovim
``` bash
brew install neovim/neovim/neovim
```
<!-- more -->

## brew 更新neovim
``` bash
brew upgrade neovim
```

## neovim 开发版本的安装
``` bash
brew tap neovim/neovim
brew install --HEAD neovim
```

## neovim安装稳定版本，不产生~/.nvimlog日志
``` bash
brew install --HEAD --with-release neovim
brew update
brew reinstall --HEAD neovim
```

##问题
如果安装过程出现问题，可以用brew doctor检查下问题。

