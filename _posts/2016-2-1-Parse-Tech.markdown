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

更新Homebrew的package数据库，在Mac的终端中输入：$ brew update
安装mongodb：$ brew install mongodb
启动mongodb：mongod --dbpath /Users/pp/LoiWu/data/db

创建app：npm init
npm install mongodb --save
创建app.js并启动：node app.js
使用mongodb查看数据库：$ mongo


