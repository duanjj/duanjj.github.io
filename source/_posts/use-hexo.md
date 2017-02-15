---
title: Hexo + Github Pages搭建博客
date: 2013-12-27 20:26:22
---
要使用Hexo，需要在你的系统中支持Nodejs以及Git，如果还没有，请自行先安装！且这里主要是针对Mac OS系统。

### 安装Hexo

``` bash
$ npm install hexo-cli -g
```

hexo全局安装一次就够了，后面可以直接使用hexo相关的操作。

### 初始化Hexo

``` bash
$ hexo init [folder]
```

新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

<!-- more -->

### 安装依赖

``` bash
$ npm install
```

安装hexo需要的一些依赖包。

### 启动Hexo

``` bash
$ hexo server
```

 启动本地web服务，用于博客的预览;成功启动后方可访问: [http://localhost:4000](http://localhost:4000/)

### Hexo的一些常用命令

**新建文章**
``` bash
$ hexo new <title>
```

此时在source文件夹中便会多出一个文档"title.md".

**生成静态页面**
``` bash
$ hexo generate (也可用简写 hexo g)
```

该命令用于生产静态文件，生成的静态内容在public文件夹内。

**清除生成内容**
``` bash
$ hexo clean
```

执行此操作会清除缓存文件 (db.json) 和已生成的静态文件 (public)。

**部署Hexo**
``` bash
$ hexo deploy（也可用简写hexo d）
```

部署播客到远端平台（比如github, heroku等平台）

**调试模式启动hexo**
``` bash
$ hexo --debug
```

### 常用简写
``` bash
$ hexo n == hexo new
$ hexo g == hexo generate
$ hexo s == hexo server
$ hexo d == hexo deploy
```

### 常用组合
``` bash
$ hexo d -g #生成部署
$ hexo s -g #生成预览
```

### 本博客用的themes
[hexo-theme-even](https://github.com/ahonn/hexo-theme-even)