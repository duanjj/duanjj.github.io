---
title: mac下使用 tree 命令在终端查看目录树结构
date: 2014-09-26 20:26:22
tags:
---
mac 下使用 *[brew包管理工具](http://brew.sh/index_zh-cn.html)* 安装 tree。

### 安装tree

``` bash
$ brew install tree
```

``` 
==> Downloading https://homebrew.bintray.com/bottles/tree-1.7.0.el_capitan.bottle.1.tar.gz
######################################################################## 100.0%
==> Pouring tree-1.7.0.el_capitan.bottle.1.tar.gz
🍺  /usr/local/Cellar/tree/1.7.0: 7 files, 113.1K
```

### 如何使用

<!-- more -->

安装成功后,直接在终端使用, 使用 --help 查看帮助信息
``` 
─djs@DonymatoMacBook-Pro  ~ ‹ruby-2.0.0› 
╰─$ tree --help                                                                                                                                                
usage: tree [-acdfghilnpqrstuvxACDFJQNSUX] [-H baseHREF] [-T title ]
    [-L level [-R]] [-P pattern] [-I pattern] [-o filename] [--version]
    [--help] [--inodes] [--device] [--noreport] [--nolinks] [--dirsfirst]
    [--charset charset] [--filelimit[=]#] [--si] [--timefmt[=]<f>]
    [--sort[=]<name>] [--matchdirs] [--ignore-case] [--] [<directory list>]
  ------- Listing options -------
  -a            All files are listed.
  -d            List directories only.
  -l            Follow symbolic links like directories.
  -f            Print the full path prefix for each file.
  -x            Stay on current filesystem only.
  -L level      Descend only level directories deep.
  -R            Rerun tree when max dir level reached.
  -P pattern    List only those files that match the pattern given.
  -I pattern    Do not list files that match the given pattern.
  --ignore-case Ignore case when pattern matching.
  --matchdirs   Include directory names in -P pattern matching.
  --noreport    Turn off file/directory count at end of tree listing.
  --charset X   Use charset X for terminal/HTML and indentation line output.
  --filelimit # Do not descend dirs with more than # files in them.
  --timefmt <f> Print and format time according to the format <f>.
  -o filename   Output to file instead of stdout.
  -------- File options ---------
  -q            Print non-printable characters as '?'.
  -N            Print non-printable characters as is.
  -Q            Quote filenames with double quotes.
  -p            Print the protections for each file.
  -u            Displays file owner or UID number.
  -g            Displays file group owner or GID number.
  -s            Print the size in bytes of each file.
  -h            Print the size in a more human readable way.
  --si          Like -h, but use in SI units (powers of 1000).
  -D            Print the date of last modification or (-c) status change.
  -F            Appends '/', '=', '*', '@', '|' or '>' as per ls -F.
  --inodes      Print inode number of each file.
  --device      Print device ID number to which each file belongs.
  ------- Sorting options -------
  -v            Sort files alphanumerically by version.
  -t            Sort files by last modification time.
  -c            Sort files by last status change time.
  -U            Leave files unsorted.
  -r            Reverse the order of the sort.
  --dirsfirst   List directories before files (-U disables).
  --sort X      Select sort: name,version,size,mtime,ctime.
  ------- Graphics options ------
  -i            Don't print indentation lines.
  -A            Print ANSI lines graphic indentation lines.
  -S            Print with CP437 (console) graphics indentation lines.
  -n            Turn colorization off always (-C overrides).
  -C            Turn colorization on always.
  ------- XML/HTML/JSON options -------
  -X            Prints out an XML representation of the tree.
  -J            Prints out an JSON representation of the tree.
  -H baseHREF   Prints out HTML format with baseHREF as top directory.
  -T string     Replace the default HTML title and H1 header with string.
  --nolinks     Turn off hyperlinks in HTML output.
  ---- Miscellaneous options ----
  --version     Print version and exit.
  --help        Print usage and this help message and exit.
  --            Options processing terminator.
```

目录遍历时使用 -L 参数指定遍历层级:
```
─djs@DonymatoMacBook-Pro  ~/workspace/test ‹ruby-2.0.0› 
╰─$ tree -L 2
.
├── app.js
├── bin
│   └── www
├── node_modules
│   ├── ansicolors
│   ├── bluebird
│   ├── buffer-shims
│   ├── cardinal
│   ├── core-util-is
│   ├── cross-env
│   ├── cross-spawn
│   ├── denque
│   ├── depd
│   ├── dottie
│   ├── esprima
│   ├── generate-function
│   ├── generic-pool
│   ├── iconv-lite
│   ├── inflection
│   ├── inherits
│   ├── isarray
│   ├── isexe
│   ├── lodash
│   ├── long
│   ├── lru-cache
│   ├── moment
│   ├── moment-timezone
│   ├── ms
│   ├── mysql2
│   ├── named-placeholders
│   ├── node-uuid
│   ├── object-assign
│   ├── process-nextick-args
│   ├── pseudomap
│   ├── readable-stream
│   ├── redeyed
│   ├── retry-as-promised
│   ├── safe-buffer
│   ├── semver
│   ├── seq-queue
│   ├── sequelize
│   ├── shimmer
│   ├── sqlstring
│   ├── string_decoder
│   ├── terraformer
│   ├── terraformer-wkt-parser
│   ├── toposort-class
│   ├── util-deprecate
│   ├── validator
│   ├── which
│   ├── wkx
│   └── yallist
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
└── routes
    ├── index.js
    └── users.js

55 directories, 5 files
```

一目了然，非常漂亮！






