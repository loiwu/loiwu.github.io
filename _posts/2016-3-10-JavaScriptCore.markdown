---
layout: post
title:  "JavaScript Core"
date:   2016-3-10 9:15:00 +0800
published:  true
categories: my projects
---

JSBase

（1）JavaScript引擎接口
JSContextGroupRef - 一组相互关联的JavaScript上下文
JSContextRef - 一个JavaScript执行上下文
JSGlobalContextRef - 一个全局的JavaScript执行上下文
JSStringRef - UTF16字符buffer，代表JavaScript
JSClassRef - JavaScript类
JSPropertyNameArrayRef - 包含JavaScript属性名的数组
JSPropertyNameAccumulatorRef - 有序集合，存储JavaScript对象的属性名
（2）JavaScript数据类型
JSValueRef - JavaScript值的基础类型，以及与这些类型相关的多态函数
JSObjectRef - JavaScript对象

JSEvaluateScript - 执行JavaScript字符串
JSCheckScriptSyntax - 检查JavaScript字符串语法
JSGarbageCollect - 执行JavaScript垃圾收集

------

JSContext

JSContext的实例代表一个JavaScript的执行环境，执行JavaScript的一切行为都在这里发生。
通过JavaScript虚拟机，JSContext可以管理JavaScript对象的生命周期。
通过强引用，JSValue的实例与JSContext相关联。只要JSValue没有销毁，它就保留着JSContext的引用。
除非JSContext被提前retain，否则它会随着所有JSValue引用的释放而释放。



------

JSExport
JSExport提供了一种声明方式，Objective-C的实例方法、类方法、属性，可以以这种方式暴露给JavaScript代码

JSExportAs(PropertyName, Selector)
当选择子被暴露给JavaScript时，进行重命名

JSVirtualMachine
JSVirtualMachine的实例代表一个JavaScript对象空间或者可执行资源的集合，支持线程安全

- (void)addManagedReference:(id)object withOwner:(id)owner;
通知JSVirtualMachine外部对象关系

- (void)removeManagedReference:(id)object withOwner:(id)owner;
通知JSVirtualMachine之前的对象关系已经不存在

