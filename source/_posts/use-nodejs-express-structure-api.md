---
title: 用Express框架构建API
date: 2015-11-22 16:56:54
tags:
---

假设这里已经安装了 [Node.js](https://nodejs.org/en/#download)，如何安装请参考官网。

### 方法一(手动创建工程)

创建web应用目录
``` bash
$ mkdir myapp
$ cd myapp
```

使用 npm init 命令为应用程序创建 package.json 文件。 有关 package.json 工作方式的更多信息，请参阅 [Specifics of npm’s package.json handling](https://docs.npmjs.com/files/package.json)。
``` bash
$ npm init
```
此命令提示您输入若干项，例如应用程序的名称和版本。 现在，只需按回车键以接受其中大多数项的缺省值，但以下情况例外：

``` bash
 entry point: (index.js)
```
输入 app.js，或者您希望使用的任何主文件名称。如果希望文件名为 index.js，请按回车键以接受建议的缺省文件名。

<!-- more -->

在 app 目录中安装 Express，然后将其保存在依赖项列表中。例如：
``` bash
$ npm install express --save
```
以上命令会将 Express 框架安装在当期目录的 node_modules 目录中， node_modules 目录下会自动创建 express 目录。以下几个重要的模块是需要与 express 框架一起安装的：  

* **body-parser** - node.js 中间件，用于处理 JSON, Raw, Text 和 URL 编码的数据。  
* **cookie-parser** - 这是一个解析Cookie的工具，通过req.cookies可以获取到传过来的cookie，并把它们转成对象。  
* **multer** - node.js 中间件，用于处理 enctype="multipart/form-data"(设置表单的MINE编码)的表单数据。
``` bash
$ npm install body-parser --save
$ npm install cookie-parser --save
$ npm install multer --save
```

要暂时安装 Express 而不将其添加到依赖项列表中，请省略 --save 选项：
``` bash
$ npm install express
```

采用 --save 选项安装的 Node 模块已添加到 package.json 文件中的 dependencies 列表。 今后运行 app 目录中的 npm install 将自动安装依赖项列表中的模块。

使用以下命令运行应用程序：
``` bash
$ node app.js
```

### 方法二(Express 应用程序生成器)
可使用应用程序生成器工具 (express) 快速创建应用程序框架。
使用以下命令安装 express：
``` bash
$ npm install express-generator -g
```

使用 -h 选项显示命令选项：
``` bash
$ express -h

  Usage: express [options][dir]

  Options:

    -h, --help          output usage information
        --version       output the version number
    -e, --ejs           add ejs engine support
        --hbs           add handlebars engine support
        --pug           add pug engine support
    -H, --hogan         add hogan.js engine support
    -v, --view <engine> add view <engine> support (ejs|hbs|hjs|jade|pug|twig|vash) (defaults to jade)
    -c, --css <engine>  add stylesheet <engine> support (less|stylus|compass|sass) (defaults to plain css)
        --git           add .gitignore
    -f, --force         force on non-empty directory
```

当前工作目录中创建名为 myapp 的 Express 应用程序：

``` bash
$ express --view=jade myapp

   create : myapp
   create : myapp/package.json
   create : myapp/app.js
   create : myapp/public
   create : myapp/public/javascripts
   create : myapp/public/images
   create : myapp/routes
   create : myapp/routes/index.js
   create : myapp/routes/users.js
   create : myapp/public/stylesheets
   create : myapp/public/stylesheets/style.css
   create : myapp/views
   create : myapp/views/index.jade
   create : myapp/views/layout.jade
   create : myapp/views/error.jade
   create : myapp/bin
   create : myapp/bin/www
```
'--view=jade' 只是说view的模板采用jade格式。该参数可选。

目录层级关系如下：
``` 
─djs@DonymatoMacBook-Pro  ~/workspace/test ‹ruby-2.0.0› 
╰─$ tree -L 2
.
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.jade
    ├── index.jade
    └── layout.jade

7 directories, 8 files
```
/bin: 用于应用启动
/public: 静态资源目录
/routes：可以认为是controller（控制器）目录
/views: jade模板目录，可以认为是view(视图)目录
app.js 程序main文件

然后安装依赖项：
``` bash
$ cd myapp
$ npm install
```

如需要数据库，用已经命令安装:
``` bash
$ npm install --save sequelize sequelize-cli sqlite3 # install ORM , CLI and SQLite dialect
```

``` code
# generate models
$ node_modules/.bin/sequelize init
$ node_modules/.bin/sequelize model:create --name User --attributes username:string
$ node_modules/.bin/sequelize model:create --name Task --attributes title:string
```

在 MacOS 或 Linux 上，采用以下命令运行此应用程序：
``` bash
$ DEBUG=myapp:* npm start
```

然后在浏览器中装入 http://localhost:3000/ 以访问此应用程序。

### Commands

To obtain a list of commands:
``` bash
$ node_modules/.bin/sequelize help
```

To initialize the project:
``` bash
$ node_modules/.bin/sequelize init
```

To see how the model:create command works:
``` bash
$ node_modules/.bin/sequelize help:model:create
```

To generate a model:
``` bash
$ node_modules/.bin/sequelize model:create --name ModelName --attributes attribute1:data_type,attribute2:data_type
```


### 参考链接
[sequelize 英文使用说明](http://docs.sequelizejs.com/)
[sequelize 中文使用说明](http://itbilu.com/nodejs/npm/N1yrA4HQW.html)
[express 英文](http://expressjs.com/)
[express 中文](http://expressjs.com/)