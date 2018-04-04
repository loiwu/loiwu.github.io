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

（1）插值

文本：数据绑定最常见的形式就是使用 “{{...}}”（双大括号）的文本插值

Html：使用 v-html 指令用于输出 html 代码

属性：HTML 属性中的值应使用 v-bind 指令

表达式：Vue.js 都提供了完全的 JavaScript 表达式支持

（2）指令

指令是带有 v- 前缀的特殊属性。指令用于在表达式的值改变时，将某些行为应用到 DOM 上。

参数：参数在指令后以冒号指明。

如， v-bind 指令被用来响应地更新 HTML 属性，在这里 href 是参数，告知 v-bind 指令将该元素的 href 属性与表达式 url 的值绑定。

```
	<div id="app">
    	<pre><a v-bind:href="url">Loi的技术Blog</a></pre>
	</div>
	<script>
		new Vue({
  			el: '#app',
  			data: {
    		url: 'http://loiwu.github.io'
  			}
		})
	</script>
```

如，v-on 指令，它用于监听 DOM 事件，在这里参数是监听的事件名。

```
	<a v-on:click="doSomething">
```

修饰符：修饰符是以半角句号 . 指明的特殊后缀，用于指出一个指定应该以特殊方式绑定。

如，.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()：

```
	<form v-on:submit.prevent="onSubmit"></form>
```

3）用户输入

在 input 输入框中可以使用 v-model 指令来实现双向数据绑定，按钮的事件我们可以使用 v-on 监听事件，并对用户的输入进行响应。

4）过滤器

Vue.js 允许自定义过滤器，被用作一些常见的文本格式化。由"管道符"指示, 格式如下：

```
	<!-- 在两个大括号中 -->
	{{ message | capitalize }}
	<!-- 在 v-bind 指令中 -->
	<div v-bind:id="rawId | formatId"></div>
```

过滤器可以串联：

```
	’{{ message | filterA | filterB }}‘
```

过滤器是 JavaScript 函数，因此可以接受参数：

```
	’{{ message | filterA('arg1', arg2) }}‘
```

这里，message 是第一个参数，字符串 'arg1' 将传给过滤器作为第二个参数， arg2 表达式的值将被求值然后传给过滤器作为第三个参数。

5）缩写

（1）v-bind 缩写

Vue.js 为两个最为常用的指令提供了特别的缩写：

```
	<!-- 完整语法 -->
	<a v-bind:href="url"></a>
	<!-- 缩写 -->
	<a :href="url"></a>
```

（2）v-on 缩写

Vue.js 为两个最为常用的指令提供了特别的缩写：

```
	<!-- 完整语法 -->
	<a v-on:click="doSomething"></a>
	<!-- 缩写 -->
	<a @click="doSomething"></a>
```


