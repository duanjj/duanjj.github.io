---
title: ccat工具
date: 2013-11-24 12:08:07
tags:
---
[ccat](https://github.com/jingweno/ccat) 高亮 cat 内容

### 安装ccat
``` bash
$ brew install ccat
```


### ccat命令 alias 成 cat 命令

``` bash
$ vi ~/.zshrc 
```
打开 .zshrc文件，写入 alias cat=ccat 这行命令保存即可,如下图：

{% asset_img 0.png %}

<!-- more -->

### 没安装ccat 和cat的区别

没安装ccat时cat命令示意图：

{% asset_img 1.png %}

安装ccat后 ccat命令示意图：

{% asset_img 2.png %}

将 ccat 命令 alias 成 cat后示意图：

{% asset_img 3.png %}
