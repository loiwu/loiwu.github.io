---
title:  "前端抢手货之 Vue.js和微信小程序框架"
subtitle: "Front End Key Skills - Vue.js and Mini Program Framework"
author: "loiwu"
avatar: "img/authors/timg.jpg"
image: "img/timg.jpg"
date:   2018-04-04 1:00:00
---

前端抢手货之 Vue.js和微信小程序框架

Part A : Vue.js

Vue.js（读音 /vjuː/, 类似于 view） 是一套构建用户界面的渐进式框架。

Vue 只关注视图层，采用自底向上增量开发的设计。

Vue 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。

Vue.js 提供一个官方命令行工具 vue-cli，可用于快速搭建大型单页应用。

结合使用npm，可以对Vue.js工程进行初始化并运行。

1）Vue.js 目录结构

:-|:-
 目录/文件|说明
 build|项目构建(webpack)相关代码
 config|配置目录，包括端口号等
 node_modules|npm 加载的项目依赖模块
 src|开发目录。包含：assets，components，router，App.vue，main.js
 static|静态资源目录，如图片、字体等
 test|初始测试目录
 .xxxx文件|这些是一些配置文件，包括语法配置，git配置等
 index.html|首页入口文件，你可以添加一些 meta 信息或统计代
 package.json|项目配置文件
 README.md|项目的说明文档，markdown 格式


2）Vue.js 起步

每个 Vue 应用都需要通过实例化 Vue 来实现。

```
var vm = new Vue({
  // 选项
})
```

 Vue 构造器中有一个el 参数，它是 DOM 元素中的 id，data 用于定义属性，methods 用于定义的函数，{{ }} 用于输出对象属性和函数返回值。

 当一个 Vue 实例被创建时，它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有的属性。当这些属性的值发生改变时，html 视图将也会产生相应的变化。

 除了数据属性，Vue 实例还提供了一些有用的实例属性与方法。它们都有前缀 $，以便与用户定义的属性区分开来。

3）Vue.js 模板语法

Vue.js 使用了基于 HTML 的模版语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。

Vue.js 的核心是一个允许你采用简洁的模板语法来声明式的将数据渲染进 DOM 的系统。

结合响应系统，在应用状态改变时， Vue 能够智能地计算出重新渲染组件的最小代价并应用到 DOM 操作上。


