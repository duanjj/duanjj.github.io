---
title: nvm(npm包管理工具)
date: 2015-11-24 20:26:22
tags:
---
### Mac OSX 

1. 使用 brew 安裝 NVM
``` bash
$ brew install nvm
```
2. 安装成功后，将下面指令加入到.bash_profile（或 .bashrc）我用的是.zshrc文件中
``` code
export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh
```
3. 重新载入上述文件
``` bash
$ source ~/.zshrc （或者 ~/.bash_profile 或 ~/bashrc）
```
4. 检测nvm
``` bash
$ nvm --version
```

### 使用 NVM 安裝 Node.js

**找出目前所有可安裝的 Node.js 版本**
``` bash
$ nvm ls-remote

    v0.11.8
    v0.11.9
    v0.11.10
    v0.11.11
    v0.11.12
    v0.11.13
    v0.11.14
    v0.11.15
    v0.11.16
    ...
    v6.8.0
    v6.8.1
    v6.9.0   (LTS: Boron)
    v6.9.1   (LTS: Boron)
    v6.9.2   (Latest LTS: Boron)
    v7.0.0
    v7.1.0
    v7.2.0
    v7.2.1
    v7.3.0
```

**安裝 Node.js (v6.9.0)**
``` bash
$ nvm install v6.9.0
```

**nvm指定使用Node.js版本**
``` bash
$ nvm use v6.9.0
Now using node v6.9.0 (npm v3.10.8)
```

**指定默认使用的版本**
``` bash
$ nvm alias default v6.9.
default -> v6.9.0
```

**列出所有安裝的版本**
``` bash
$ nvm ls
->       v6.9.0
         v6.9.2
         system
default -> v6.9.0
node -> stable (-> v6.9.2) (default)
stable -> 6.9 (-> v6.9.2) (default)
iojs -> N/A (default)
lts/* -> lts/boron (-> v6.9.2)
lts/argon -> v4.7.0 (-> N/A)
lts/boron -> v6.9.2
```

**測試 Node.js**
``` bash
$ node -v
v6.9.2
```

**測試 npm**
``` bash
$ npm -v
3.10.9
```

### 配置 npm 源（可选）
nvm 安装 node 的同时会安装 npm。但是，国外源的速度和稳定性毕竟不让人放心。淘宝为大家提供了一个完整 npm 镜像 http://npm.taobao.org/。
我们可以使用淘宝提供的 ***cnpm*** 替代 ***npm*** 使用：
``` bash
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

这样安装模块的时候:
``` bash
$ cnpm install [name]
```
使用的就是淘宝的源了。 它支持除了 npm publish 之外的所有命令。

### 使用 .nvmrc 文件配置项目所使用的 node 版本
每个版本的Node都会自带一个不同版本的npm，可以用npm -v来查看npm的版本。全局安装的npm包并不会在不同的Node环境中共享，因为这会引起兼容问题。它们被放在了不同版本的目录下，例如~/.nvm/versions/node/<version>/lib/node_modules</version>这样的目录。这刚好也省去我们在Linux中使用sudo的功夫了。因为这是用户的主文件夹，并不会引起权限问题。
如果默认 node 版本（通过 nvm alias 命令设置的）与项目所需的版本不同，则可在项目根目录或其任意父级目录中创建 .nvmrc 文件，在文件中指定使用的 node 版本号，如：
``` bash
$ touch .nvmrc
$ echo 5.9.0 > .nvmrc
```

进入当前项目后，运行如下命令即可切换到该项目对应的node版本
``` bash
$ nvm use 
Found '/Users/djs/work/jasduaner-blog/.nvmrc' with version <v6.9.2>
Now using node v6.9.2 (npm v3.10.9)
```

### 参考资料
[Mac OSX Install](http://mac-osx-for-newbie-book.kejyun.com/software/softwareWebDeveloperNodeJS.html)
[nvm](https://github.com/creationix/nvm)
