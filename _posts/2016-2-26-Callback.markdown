---
layout: post
title:  "iOS中的Delegation, Notification 和 Observation"
date:   2016-2-26 9:15:00 +0800
published:  true
categories: my projects
---

原文链接[When to use Delegation, Notification, or Observation in iOS](http://blog.shinetech.com/2011/06/14/delegation-notification-and-observation/)

在iOS开发中，常会遇到这样的问题：如何能在不过度耦合的情况下实现控制器之间的通信。

通常采用以下三种模式：
1. Delegation 代理
2. Notification Center 通知中心
3. Key value observing 键值监听

以下的总结来自我iOS应用开发的实际经验。我将探讨：
1. 为什么某种模式比另一种模式好
2. 为什么在特定场景下某种模式更适合

这三种模式都可以完成控制器间的通信。

代理 Delegation
控制器通过订立协议（protocol，方法集合的定义），协议描述的代理对象为了响应控制器的响应事件，从而需要执行的各种方法。
控制器可以通过它的代理响应相关的方法调用。
优点：
- 语法严格，所有事件都可以被监控并且在协议中清晰的定义
- 如果需要实现的代理方法没有被正确实现，在编译期间会收到警告/错误
- 协议的定义限于控制器范围内
- 在程序中易于追踪和确定控制流程
- 一个控制器可以相应多个协议，每个协议可以有不同的代理
- 通信过程中不需要维护其他对象
- 可以接收被调用协议方法的返回值，所以代理可以向控制器提供返回信息
缺点：
- 繁琐的定义：定义协议、定义控制器的delegate属性、在代理中实现相应的代理方法
- 释放对象时，要求正确释放代理。对已经释放的对象调用相关代理方法会造成程序奔溃
- 难以实现多对一的响应

通知 Notifications
通知中心采用单例模式，可以通知对象事件的发生。通过通知，可以实现松耦合的控制器与对象的通信。
控制器以通知名称作为key，监听特定事件的发生。通过注册通知名称，相应对象可以对通知事件进行响应。
优点：
- 易实现，代码量少
- 轻松实现多对一的响应
- 通知抛出时，可传递参数给监听者
缺点：
- 编译期间不会检查停止是否被观察者正确响应
- 在释放对象时需要移出通知监听
- 不易追踪，难以通过应用流程和控制进行调试
- 需要锅里控制器和观察者的连接对象
- 通知名称，用户信息字典键名称，都需要被控制器和观察者得知，定义是需要留心
- 通知发出后，控制器收不到观察者的反馈

观察者 Observation
键值监听KVO可以实现对象对另一个对象属性发生改变的监听。
代理和通知适合控制器与任意其它对象的通信，KVO适合任何类型对象对其它任意对象改变的监听。这种模式适用于对象间的信息同步。
KVO只能被应用在对象属性改变的监听上
优点：
- 高效实现了两种对象之间的信息同步，如数据模型和视图
- 轻松实现对对象内状态改变的响应
- 可以同时提供原始值和新值
- 可以通过关键路径来监听属性，复合属性也可以被监听
- 对象的完全监听，不需要辅助编码
缺点：
- 被监听的属性需要用字符串定义，编译时不会进行错误检测
- 属性的重构会导致观察者代码失效
- 如果一个对象正在监听多个值，带来繁琐的“IF”判断
- 当对象被释放时需要移出观察者

总结
三种模式都存在各自的优缺点，都是其适用的场景。三种模式都是对象对其它对象进行事件通知的方式。
KVO拥有较为明确的适用场景。其余两种模式常常应用在控制器的通信中。

过度使用通知模式，会导致程序逻辑流程难以追踪。用户信息字典的键名常常会不同步，越来越多的常量被定义。
梳理流程、整理键名，会导致开发效率降低。

对于控制器间的通信，存在明确的逻辑，适宜采用命名良好的代理和代理方法定义，可以提升代码的可读性和流程的可追溯性。
修改代理协议和方法实现将会被编译器察觉。

通知适用于全局状态改变。

As a rule of thumb I will only use observation, for property level events within objects that I did not code, or for property level events within model objects that are tightly bound to a view object. For all other events, I will always try to use a delegate pattern, if for some reason I can’t do that, I will first assess whether I have something critically wrong with my app’s structure, and if not, only then will I use notifications.


