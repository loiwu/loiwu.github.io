---
title:  "Agile JavaScript Development"
subtitle: "JavaScript快速全栈开发"
author: "loiwu"
avatar: "img/authors/beACat.jpg"
image: "img/c.jpg"
date:   2018-03-10 1:00:00
---

Rapid Prototyping with JS: Agile JavaScript Development 

###  1. Basic Information

1.1 定义前端

Begin - 用户在浏览器/客户端输入或点击一个链接

-> 浏览器向服务器发送HTTP请求

-> 服务器处理请求，如果查询字符串或请求体里含有参数，服务器也会把这些参数信息考虑进去

-> 服务器更新、获取或转换数据库里的数据

-> 服务器以HTML、JSON或其他格式返回一个HTTP响应

-> 浏览器接收HTTP响应

-> 浏览器以HTML或其他格式（如JPEG、XML或JSON）把HTTP响应呈现给用户 - End

1.2 敏捷开发

（1）[Scrum](https://www.scrum.org/resources/scrum-guide)

Scrum由一个个短周期组成，每个周期叫sprint。一个sprint通常持续一到两周。典型的sprint是在sprint计划会议上开始和结束的，这些会议同时会把新任务分配给团队成员。通过sprint计划会议，新任务可以被添加到sprint里。

每天进行的scrum会议室Scrum方法体系的重要组成部分。每一个scrum会议通常是在走廊里进行的5~15分钟的会议。在scrum会议上，每一个团队成员要回答一下三个问题：
 - 自己昨天做了什么？
 - 今天准备做什么？
 - 是否需要从其他团队成员那里得到些什么？

在高度变化的环境中（如创业初期），敏捷开发显得更加灵活。其好处在于：在没办法提前规划时，或者需要以收集的用户反馈作为主要决策因素时，敏捷开发往往非常有效。

（2）测试驱动开发 TDD

 - 使用断言为新功能、新任务写下失败的自动测试用例
 - 写出能够成功通过测试的代码
 - 如果需要，重构代码，添加功能，同时保证测试用例的通过
 - 重复以上步骤直至所有任务都完成

测试可以分为功能测试和单元测试。
单元测试通过模拟依赖，测试系统单元、函数、方法。
功能测试（或称集成测试）是在包含依赖的情况下，测试一系列功能。

TDD的优点在于：更少的错误和缺陷；更有效的代码；确保在不影响已有功能的情况下，新代码能正常工作。

（3）持续部署和持续集成

持续部署（Continuous Delivery）是一系列技术的组合，可以快速把开发好的新功能、错误修复和增强功能呈现给用户。CD包含自动测试和自动部署。持续部署可以减少我们的手工劳动，尽可能地缩短收集反馈的时间。

以下是流行的持续集成解决方案：
 
 - [Jenkins](https://jenkins.io/)：开源的可扩展持续集成服务器
 - [CircleCI](https://circleci.com/)：更好更快的代码
 - [Travis CI](https://travis-ci.org/)：一个针对开源社区的持续集成托管服务

参考：[Continuous Delivery vs Continuous Deployment vs Continuous Integration: Key Definitions](https://blog.assembla.com/assemblablog/tabid/12618/bid/92411/continuous-delivery-vs-continuous-deployment-vs-continuous-integration-wait-huh.aspx)

（4）结对编程

结对编程是两个开发者在同一个环境里一起工作的技术。其中一个开发者是“驾驶员”，另一个是“观察员”。驾驶员主要负责写代码，观察员围观并且提供建议。一段时间后两人互换角色。驾驶员的角色更关注当下的任务，观察员需要有大局观，发现错误并且改进算法。

结对编程的特点：
 
 - 两人可以一起产出更简洁、更高效的代码，同时降低引发错误和缺陷的几率
 - 程序员们在一起工作时，可以彼此交流和传递知识，但也可能发生冲突，而且这并不少见

 1.3 定义后端

 （1）[Node.js](https://nodejs.org/en/)

 Node.js是事件驱动异步I/O开源程序，可以用来创建可伸缩且高性能的Web服务器。Node.js由Google的[V8 JavaScript引擎](https://en.wikipedia.org/wiki/Chrome_V8)组成，并由云服务公司[Joyent](https://www.joyent.com/)维护。

 使用Node.js的优势：

  - JavaScript语言作为Web和移动开发的业界标准，开发人员熟悉他的可能性更高
  - 前后端用同一种编程语言进行开发，可以加快写代码的过程。开发者的思维不需要在不同的语法间切换，可以更快地学习各种方法和类
  - 使用Node.js可以快速地搭建原型，做市场开发，提前获取用户。与使用PHP或者MySQL的等不太敏捷的技术的公司相比，这是很重要的优势
  - Node.js可以通过[WebSocket](https://en.wikipedia.org/wiki/WebSocket)支持实时应用程序

（2）NoSQL和MongoDB

[MongoDB](https://www.mongodb.com/)是可用于大数据的高性能非关系型数据库。由于传统的关系型数据库管理系统（RDBMS）无法应对大数据的挑战，NoSQL概念应运而生。

MongoDB的优势：

 - 可伸缩性：由于其分布式特性，可以在多个服务器和数据中心防止荣誉数据
 - 高性能：MongoDB在存储和检索方面非常高效，部分原因是数据库中元素与集合之间关系上的弱处理
 - 灵活性：键-值对的存储非常适合原型开发，因为使用它的用户，不需要关系表关系，不需要修复数据模型，不需要关注复杂的数据迁移

（3）云计算

云计算由以下服务组成：

 - 基础设施即服务 IaaS
 - 平台及服务 PaaS
 - 后端即服务 BaaS
 - 软件即服务 SaaS

云应用平台具备以下功能：

 - 可伸缩性，例如在几分钟内产生新的实例
 - 部署简单，如想Heroku部署，只需要 $ git push
 - 现收现付制，用户根据需要添加和删除内存及磁盘空间
 - 可扩展，方便安装和设置数据库、应用服务器、程序包等
 - 安全和技术支持

PaaS和BaaS非常适合构建原型，一般用来创建MVP（Minimal Viable Product，最小化可行的产品），供那些尚处于创业初始阶段的团队使用。

我体验过的PaaS提供商：[Heroku](https://www.heroku.com/)

（4）HTTP请求和响应

每一个HTTP请求和响应均由以下组件构成：
 
 - 头部（header）：关于编码、主体的长度、来源、内容类型等的信息
 - 主体（body）：内容，一般是参数或数据，通常传递给服务器，或返回给客户端

HTTP请求包含以下几方面内容：

 - 方法：一些请求方法，如常见的GET、POST、PUT、DELETE
 - URL：主机、端口和路径，如http://loiwu.github.io/#/2016/04/28/be-a-tiger
 - 查询字符串：URL里问好之后的所有字符，比如 ?k=直播+Live

（5）[REST](https://en.wikipedia.org/wiki/Representational_state_transfer)式API

由于在分布式系统中每个事物都需要包含足够多关于客户端状态的信息，REST（REpresentational State Transfer）式API因此流行起来。从某种意义上来说，这个标准也是无状态的，因为客户端的状态并不会保存在服务器上，这样才使得每一个请求可以分发到不同的服务系统上进行处理。

REST式API的特征：
 
 - 有更好的可伸缩性，因为它支持把不同的组件部署到不同的服务器上
 - 替代SOAP（Simple Object Access Protocol，简单对象访问协议），因为它是简单的动词和名词组合
 - 充分利用HTTP方法，如GET、POST、DELETE、PUT、OPTIONS等

REST不是一种协议，而是一种比诸如SOAP这样的协议更灵活的架构。

参考：

[A Brief Introduction to REST](https://www.infoq.com/articles/rest-introduction)

[幂等方法](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Idempotent_methods_and_web_applications)



### 2. 环境搭建

2.1 本地环境搭建

0）逐步安装本地组件。

 - 开发目录

 - 浏览器

 - IDE

 - 版本控制

 - 本地HTTP服务器

 - 数据库，如MongoDB

 - 组件，如 Node.js、JS库（LESS/Bootstrap/jQuery/Backbone.js）等

2.2 云端环境搭建

0）为使用云服务做准备。

 - SSH密钥

 - 代码仓库: [GitHub](https://github.com/)/[Bitbucket](https://bitbucket.org/)/[GitLab](https://about.gitlab.com/)

 - 云主机

 - [Heroku](https://www.heroku.com/)

 - [Cloud9](https://aws.amazon.com/cn/cloud9/)
 
 
 
 ### 3. END
