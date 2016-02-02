---
layout: post
title:  "GWRabbit 技术仓库"
date:   2016-2-1 12:15:00 +0800
published:  true
categories: my projects
---

#技术

*    Parse开源SDK

看这篇文档做初步了解：http://blog.parse.com/learn/the-parse-sdk-whats-inside/

*    Bolts

看这篇文档：http://blog.parse.com/announcements/lets-bolt/

这是[Bolts的Github主页](https://github.com/BoltsFramework)

看这里https://github.com/BoltsFramework/Bolts-iOS，了解Bolts的细节

*    APPLINKS

在Bolts中，采用了这项快平台并且开源的移动端Deep-link技术[APPLINKS](http://applinks.org/)

#开发

Android开发使用Android Studio，[下载链接](http://developer.android.com/sdk/index.html)

#进展

2016年2月1日开始撰写该文档

#需要弄清楚的问题

1 - 搭建Parse Server涉及的技术

*    Node.js
*    Express
*    MangoDB
*    Python
*    Heroku

2 - 使用Parse SDK涉及的问题

*    Bolts
*    APPLINKS
*    Android开发
*    Java
*    Parse SDK

3 - 产品设计

*    Sketch
*    产品设计方法
*    商业模式
*    运营模式

#弄清楚以上问题的过程

为了弄清楚如何搭建后台，我于2016年2月1日开始学习下面这本书：
Web Development with MongoDB and NodeJS

我做了以下学习笔记：

A short introduction to Node.js
Node.js可以被视为构建在谷歌V8引擎智商的JavaScript运行时环境。所以只要是能安装Node.js的平台，都可以运行JavaScript。
npm – the Node Package Manager
Node的包管理器

MongoDB
更新Homebrew的package数据库，在Mac的终端中输入：$ brew update
安装mongodb：$ brew install mongodb
启动mongodb：mongod --dbpath /Users/pp/LoiWu/data/db
创建app：npm init
npm install mongodb --save
创建app.js并启动：node app.js
使用mongodb查看数据库：$ mongo

A JavaScript Primer
语法基础、数据类型、变量范围、运算符和流程控制、对象、数组、函数、匿名函数和回调、JSON

Node.js
Event-driven 事件驱动 和Object-Document Mapper
异步执行
模块系统
The Node.js Core，包含了以下：Events、Filesystems、HTTP、Net、Streams、Timers

通过npm安装模块
npm install ***
npm init
npm install *** --save
npm install *** --save-dev
cat package.json

MongoDB基础知识
CRUD - create, read, update, delete
$ mongo
> show dbs
> use database1
> show collections
> db.newCollection.insert()
> db.newCollection.find()
> db.newCollection.findOne()
> db.newCollection.update()
> db.newCollection.remove()
> db.newCollection.drop()

Express
Express is a minimal and  exible Node.js web application framework, providing a robust set of features for building single, multi-page, and hybrid web applications. 

制作一个完整的web应用：tigerShiny.io

Designing the web application 设计web应用，需要有需求分析报告

Organizing the  les文件组织：
/(project root)
---/helpers
---/controllers
---/public
------/css
------/img
------/js
------/upload
---/server
---/views
------/layouts
------/partials

npm init
npm install express morgan body-parser cookie-parser method-override errorhandler express-handlebars --save

Creating the application's entry point
vim server.js
node server.js
$ PORT=5500 node server.js
Server up: http://localhost:5500

Using and understanding middleware使用和理解中间件
The idea behind middleware is that it acts like a stack of  lters that every request to your server passes through. Since every request passes through each  lter, each  lter can perform a speci c task against the request before it passes through to the next  lter. Typically, these  lters are used for tasks such as cookie parsing, form  eld handling, session handling, authentication, and error handling and logging. 

中间件的调用顺序至关重要
• morgan: 负责log模块，对于Node服务器的调试很有帮助
• bodyParser: 负责表单打包的模块
• methodOverride: 旧式浏览器不支持REST HTTP verbs，比如UPDATE、PUT，method中间件负责解决该问题
• cookieParser: 允许cookies的接收和发送
• errorHandler: 处理中间件处理流程中的出错
• Handlebars: 视图的模板引擎
• express.static() middleware 








