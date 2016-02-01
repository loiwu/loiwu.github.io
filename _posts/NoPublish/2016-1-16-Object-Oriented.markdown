---
layout: post
title:  "Object Oriented Programming"
date:   2016-1-16 0:00:00 +0000
published:  false
categories: loiwu update
---

Logic will get you from A to B. Imagination will take you everywhere.

#Object Oriented Programming [面向对象编程](https://en.wikipedia.org/wiki/Object-oriented_programming)

总结高级面向对象编程的知识。当初还是外行之人的我不以为然，现在细想，这些mental toolset真的是利器，对于代码设计、逻辑思考、问题处理，都是力量之源。

##Contents

* [Features](#oop_features)
* [GoF](#oop_gof)

<b id="oop_features"></b>

###Features

####Objects and Classes 对象和类

1. Classes - the definitions for the data format and available procedures for a given type or class of object; may also contain data and procedures (known as class methods) themselves
- 类 - 给定类型对象的定义，包括对象的数据格式和可用操作

2. Objects - instances of classes
- 对象 - 类的实例

3. Terms 成员变量包括类变量和实例变量，成员方法包括类方法和实例方法

- Class variables - belong to the class as a whole; there is only one copy of each one
    - 类变量被整个类所拥有，每个类只有一份
- Instance variables or attributes - data that belongs to individual objects; every object has its own copy of each one
    - 实例变量或属性属于对象，每一个对象都拥有它自己的实例变量
- Member variables - refers to both the class and instance variables that are defined by a particular class
    - 成员变量会同时被类和特定类所定义的实例变量共同引用
- Class methods - belong to the class as a whole and have access only to class variables and inputs from the procedure call
    - 类方法被整个类所拥有，它只对类变量和过程调用的输入有存取权限
- Instance methods - belong to individual objects, and have access to instance variables for the specific object they are called on, inputs, and class variables
    - 实例方法被单个对象所拥有，对它调用的特定对象的实例变量有存取权限

###Dynamic dispatch/message passing 动态分发/消息传递

1. Dynamic dispatch - It is the responsibility of the object, not the external code, to 'on-demand' select the procedural code to run/execute in response to a method call, typically by looking up the method at run time in a table associated with the object
- 动态分发特性表现为，对象按需选择过程代码去执行，以满足方法调用。

2. Message passing - A method call is also known as message passing. It is conceptualized as a message (the name of the method and its input parameters) being passed to the object for dispatch
- 消息传递也就是方法调用。消息就是概念化的方法名和方法参数，消息被传递给对象以便分发

<b id="oop_gof"></b>

###[Design Patterns](https://en.wikipedia.org/wiki/Design_Patterns)
[设计模式](https://zh.wikipedia.org/wiki/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F%EF%BC%9A%E5%8F%AF%E5%A4%8D%E7%94%A8%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E8%BD%AF%E4%BB%B6%E7%9A%84%E5%9F%BA%E7%A1%80)

1. 创建范例
- 抽象工厂[Abstract Factory](https://zh.wikipedia.org/wiki/%E6%8A%BD%E8%B1%A1%E5%B7%A5%E5%8E%82)
- 工厂方法[Factory Method pattern](https://zh.wikipedia.org/wiki/%E5%B7%A5%E5%8E%82%E6%96%B9%E6%B3%95)

2. 结构范例

3. 行为范例

