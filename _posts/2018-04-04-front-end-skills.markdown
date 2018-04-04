---
title:  "前端抢手货之 Vue.js和微信小程序框架"
subtitle: "Front End Key Skills - Vue.js and Mini Program Framework"
author: "loiwu"
avatar: "img/authors/timg.jpg"
image: "img/timg.jpg"
date:   2018-04-04 1:00:00
---

Vue.js和微信小程序框架，还是那句话，市场行情就是这样，赶紧学吧。

========== ==========

<a target="_blank" href="https://github.com/Meituan-Dianping/mpvue"> Part A > mpvue </a>

<a target="_blank" href="https://github.com/Meituan-Dianping/mpvue">mpvue, 是基于Vue.js的小程序开发框架, 从底层支持Vue.js语法和构建工具体系</a>

========== ==========

Part A mpvue，就是重点，赶紧点开来研究代码吧，

Part B Vue.js，就是一堆非常随意的字，别看了，对你没用。

========== ==========

Part B : Vue.js，构建用户界面的渐进式框架

Vue.js（读音 /vjuː/, 类似于 view）。

Vue 只关注视图层，采用自底向上增量开发的设计。

Vue 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。

Vue.js 提供一个官方命令行工具 vue-cli，可用于快速搭建大型单页应用。

结合使用npm，可以对Vue.js工程进行初始化并运行。

一、Vue.js 目录结构

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


二、Vue.js 起步

每个 Vue 应用都需要通过实例化 Vue 来实现。

```
	var vm = new Vue({
  		// 选项
	})
```

 Vue 构造器中有一个el 参数，它是 DOM 元素中的 id，data 用于定义属性，methods 用于定义的函数，{{ }} 用于输出对象属性和函数返回值。

 当一个 Vue 实例被创建时，它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有的属性。当这些属性的值发生改变时，html 视图将也会产生相应的变化。

 除了数据属性，Vue 实例还提供了一些有用的实例属性与方法。它们都有前缀 $，以便与用户定义的属性区分开来。

三、Vue.js 模板语法

Vue.js 使用了基于 HTML 的模版语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。

Vue.js 的核心是一个允许你采用简洁的模板语法来声明式的将数据渲染进 DOM 的系统。

结合响应系统，在应用状态改变时， Vue 能够智能地计算出重新渲染组件的最小代价并应用到 DOM 操作上。

1）插值

文本：数据绑定最常见的形式就是使用 /{/{.../}/}（双大括号）的文本插值

Html：使用 v-html 指令用于输出 html 代码

属性：HTML 属性中的值应使用 v-bind 指令

表达式：Vue.js 都提供了完全的 JavaScript 表达式支持

2）指令

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
	/{/{ message | capitalize /}/}
	<!-- 在 v-bind 指令中 -->
	<div v-bind:id="rawId | formatId"></div>
```

过滤器可以串联：

```
	/{/{ message | filterA | filterB /}/}
```

过滤器是 JavaScript 函数，因此可以接受参数：

```
	/{/{ message | filterA('arg1', arg2) /}/}
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

四、Vue.js 条件与循环

1）条件判断

（1）v-if

条件判断使用 v-if 指令

（2）v-else

用 v-else 指令给 v-if 添加一个 "else" 块

（3）v-else-if

v-else-if 在 2.1.0 新增，用作 v-if 的 else-if 块，可以链式的多次使用

（4）v-show

可以使用 v-show 指令来根据条件展示元素

2）循环语句

循环使用 v-for 指令。

v-for 指令需要以 site in sites 形式的特殊语法， sites 是源数据数组并且 site 是数组元素迭代的别名。

（1）v-for 迭代对象

v-for 可以通过一个对象的属性来迭代数据，也可以提供第二个的参数为键名，第三个参数为索引。

（2）v-for 迭代整数

v-for 也可以循环整数。

五、Vue.js 计算属性

计算属性关键词: computed。

可以使用 methods 来替代 computed，效果上两个都是一样的，但是 computed 是基于它的依赖缓存，只有相关依赖发生改变时才会重新取值。

而使用 methods ，在重新渲染的时候，函数总会重新调用执行。可以说使用 computed 性能会更好，但是如果不希望缓存，那可以使用 methods 属性。

computed setter：computed 属性默认只有 getter ，不过在需要时也可以提供一个 setter

六、Vue.js 监听属性

可以通过 watch 来响应数据的变化

七、Vue.js 样式绑定

1）Vue.js class

class 与 style 是 HTML 元素的属性，用于设置元素的样式，可以用 v-bind 来设置样式属性。

Vue.js v-bind 在处理 class 和 style 时， 专门增强了它。表达式的结果类型除了字符串之外，还可以是对象或数组。

2）class 属性绑定

可以为 v-bind:class 设置一个对象，从而动态的切换 class

```
	<!-- 实例中将 isActive 设置为 true 显示了一个绿色的 div 块，如果设置为 false 则不显 -->
	<div v-bind:class="{ active: isActive }"></div>
	<!-- 以上实例 div class 为 -->
	<div class="active"></div>
```

数组语法

```
	<!-- 我们可以把一个数组传给 v-bind:class -->
	<div v-bind:class="[activeClass, errorClass]"></div>
```

3）Vue.js style(内联样式)

可以在 v-bind:style 直接设置样式

八、Vue.js 事件处理器

事件监听可以使用 v-on 指令。

1）事件修饰符：Vue.js 为 v-on 提供了事件修饰符来处理 DOM 事件细节，如：event.preventDefault() 或 event.stopPropagation()。

Vue.js通过由点(.)表示的指令后缀来调用修饰符。

```
	.stop
	.prevent
	.capture
	.self
	.once
```

```
	<!-- 阻止单击事件冒泡 -->
	<a v-on:click.stop="doThis"></a>
	<!-- 提交事件不再重载页面 -->
	<form v-on:submit.prevent="onSubmit"></form>
	<!-- 修饰符可以串联  -->
	<a v-on:click.stop.prevent="doThat"></a>
	<!-- 只有修饰符 -->
	<form v-on:submit.prevent></form>
	<!-- 添加事件侦听器时使用事件捕获模式 -->
	<div v-on:click.capture="doThis">...</div>
	<!-- 只当事件在该元素本身（而不是子元素）触发时触发回调 -->
	<div v-on:click.self="doThat">...</div>
	<!-- click 事件只能点击一次，2.1.4版本新增 -->
	<a v-on:click.once="doThis"></a>
```

2）按键修饰符

Vue 允许为 v-on 在监听键盘事件时添加按键修饰符。

```
	<!-- 只有在 keyCode 是 13 时调用 vm.submit() -->
	<input v-on:keyup.13="submit">
```

记住所有的 keyCode 比较困难，所以 Vue 为最常用的按键提供了别名：

```
	<!-- 同上 -->
	<input v-on:keyup.enter="submit">
	<!-- 缩写语法 -->
	<input @keyup.enter="submit">
```

全部的按键别名：

```
	.enter
	.tab
	.delete (捕获 "删除" 和 "退格" 键)
	.esc
	.space
	.up
	.down
	.left
	.right
	.ctrl
	.alt
	.shift
	.meta
```

```
	<p><!-- Alt + C -->
	<input @keyup.alt.67="clear">
	<!-- Ctrl + Click -->
	<div @click.ctrl="doSomething">Do something</div>
```

九、Vue.js 表单

用 v-model 指令在表单控件元素上创建双向数据绑定。

<div class="scale"><img src="img/resources/vuejsimg/vuejs-sheet.png"  alt="Vue.js 表单" /></div>

十、Vue.js 组件

组件（Component）是 Vue.js 最强大的功能之一。

组件可以扩展 HTML 元素，封装可重用的代码。

组件系统让我们可以用独立可复用的小组件来构建大型应用，几乎任意类型的应用的界面都可以抽象为一个组件树：

<div class="scale"><img src="img/resources/vuejsimg/vuejs-components.png"  alt="Vue.js 组件" /></div>

十一、Vue.js 自定义指令

除了默认设置的核心指令( v-model 和 v-show ), Vue 也允许注册自定义指令。

十二、Vue.js 路由

Vue.js 路由允许我们通过不同的 URL 访问不同的内容。

通过 Vue.js 可以实现多视图的单页Web应用（single page web application，SPA）。

[vue-router 库](https://github.com/vuejs/vue-router)

[vue-router文档](https://router.vuejs.org/zh-cn/)
