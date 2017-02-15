---
title: Setup Ruby On Rails on macOS
date: 2013-02-23 20:26:22
tags:
---
主要介绍在macOS系统上如何安装ruby on rails环境。

### Installing Homebrew
``` bash
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Installing Ruby
**1. 用 [rbenv](https://github.com/rbenv/rbenv) 来安装ruby**
``` bash
$ brew install rbenv ruby-build

# 添加rbenv bash,这样就不用重新再打开一个终端
$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
$ source ~/.bash_profile

$ rbenv install 2.0.0       # intall ruby (这个过程会花点时间，需耐心等待)
$ rbenv global 2.0.0        # sets the default version of Ruby
$ ruby -v                   # check ruby version
# ruby 2.0.0p643            # 出现类似这样的提示，说明已经成功安装了ruby,且版本为 2.0.0p643
```

<!-- more -->

**rbenv其他命令**
``` bash
$ rbenv versions             # 列出安装的版本
$ rbenv version              # 列出正在使用的版本
$ rbenv global 1.9.3-p392    # 默认使用 1.9.3-p392
$ rbenv shell 1.9.3-p392     # 当前的 shell 使用 1.9.3-p392, 会设置一个`RBENV_VERSION` 环境变量
$ rbenv local jruby-1.7.3    # 当前目录使用 jruby-1.7.3, 会生成一个 `.rbenv-version` 文件
```

**rbenv 下使用 gemset**
rvm 中最方便的就是 gemset。rbenv 通过插件也可以使用 gemset。
``` bash
$ brew install rbenv-gemset  # 
```

**创建一个 gemset**
``` bash
$ rbenv gemset create 1.9.3-p392 ruby-china
                       参数 1       参数 2
```
以上命令中，参数 1 是已安装的 ruby 版本，参数 2 是 gemset 的名字

**使用方法**
在项目的根目录下，把想要使用的gemset名字放到.rbenv-gemsets文件中即可。有.rbenv-gemsets文件的情况下执行 bundle 命令就是对设置好的 gemset 进行操作。

``` bash
$ echo ruby-china > .rbenv-gemsets
```
当前目录下没有 .rbenv-gemsets 文件的情况下，执行 bundle 命令（没有指定 --path 参数的情况）时，是对当前版本的 ruby 版本的 gemset 。也就相当于 rvm 中 global gemset 的作用了。

**参考**
[rbenv-gemset (github)](https://github.com/jamis/rbenv-gemset)

**2. 用 [RVM](https://rvm.io/) 来安装ruby**
RVM 是一个命令行工具，可以提供一个便捷的多版本 Ruby 环境的管理和切换。

**Ruby 的安装与切换**
``` bash
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
$ \curl -sSL https://get.rvm.io | bash -s stable
$ source ~/.bashrc
$ source ~/.bash_profile

# 修改 RVM 的 Ruby 安装源到 Ruby China 的 Ruby 镜像服务器，这样能提高安装速度
$ echo "ruby_url=https://cache.ruby-china.org/pub/ruby" > ~/.rvm/user/db

# 列出已知的 Ruby 版本
$ rvm list known

# 安装一个 Ruby 版本
$ rvm install 2.0.0 --disable-binary  # 这里安装了ruby 2.0.0的版本, rvm list known 列表里面的都可以拿来安装。

# 查询已经安装的ruby
$ rvm list

# 卸载一个已安装版本
$ rvm remove 1.8.7
```

**gemset 的使用**
RVM 不仅可以提供一个多 Ruby 版本共存的环境，还可以根据项目管理不同的 gemset。

gemset 可以理解为是一个独立的虚拟 Gem 环境，每一个 gemset 都是相互独立的。

比如你有两个项目，一个是 Rails 2.3 一个是 rails3. gemset 可以帮你便捷的建立两套 Gem 开发环境，并且方便的切换。

gemset是附加在 Ruby 语言版本下面的，例如你用了 1.9.2, 建立了一个叫 rails3 的gemset,当切换到 1.8.7 的时候，rails3 这个 gemset 并不存在。

**建立 gemset**
``` bash
$ rvm use 1.8.7
$ rvm gemset create rails23
```
然后可以设定已建立的 gemset 做为当前环境。

**use 可以用来切换语言或者 gemset**
前提是他们已经被安装(或者建立)。并可以在 list 命令中看到。

``` bash
$ rvm use 1.8.7
$ rvm use 1.8.7@rails23
```
然后所有安装的 Gem 都是安装在这个 gemset 之下

**列出当前 Ruby 的 gemset**
``` bash
$ rvm gemset list
```

**清空 gemset 中的 Gem**
如果你想清空一个 gemset 的所有 Gem, 想重新安装所有 Gem，可以这样

``` bash
$ rvm gemset empty 1.8.7@rails23
```

**删除一个 gemset**
``` bash
$ rvm gemset delete rails2-3
```

**项目自动加载 gemset**
RVM 还可以自动加载 gemset。
例如我们有一个 Rails 3.1.3 项目，需要 1.9.3 版本 Ruby，整个流程可以这样。
``` bash
$ rvm install 1.9.3
$ rvm use 1.9.3
$ rvm gemset create rails313
$ rvm use 1.9.3@rails313
```
下面进入到项目目录，建立一个 .rvmrc 文件。

在这个文件里可以很简单的加一个命令：
``` bash
$ rvm use 1.9.3@rails313
```

然后无论你当前 Ruby 设置是什么，cd 到这个项目的时候，RVM 会帮你加载 Ruby 1.9.3 和 rails313 gemset.















