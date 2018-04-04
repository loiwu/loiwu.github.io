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

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title>Vue.js App -（loiwu.github.io)</title>
	<script src="https://cdn.bootcss.com/vue/2.4.2/vue.min.js"></script>
</head>
<body>
    <div id="vue_det">
        <h1>site : {{site}}</h1>
        <h1>url : {{url}}</h1>
        <h1>Alexa : {{alexa}}</h1>
    </div>
    <script type="text/javascript">
    // 数据对象
    var data = { site: "TechBlog", url: "loiwu.github.io", alexa: 100}
    var vm = new Vue({
        el: '#vue_det',
        data: data
    })
    // 引用相同的对象！
    document.write(vm.a === data.a) // true
	document.write("<br>")
    // 设置属性也会影响到原始数据
    vm.site = "TechBlog"
    document.write(data.site + "<br>") // TechBlog
    // ……反之亦然
    data.alexa = 1001
    document.write(vm.alexa) // 1001
	document.write("<br>")
	document.write(vm.$data === data) // true
    document.write("<br>")
    document.write(vm.$el === document.getElementById('vue_det')) // true
    </script>
</body>
</html>
```



