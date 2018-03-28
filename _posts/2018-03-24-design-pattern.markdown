---
title:  "指导日常工作的设计模式和架构模式总结"
subtitle: "Design Pattern & Architectural Pattern"
author: "loiwu"
avatar: "img/authors/metiger.jpg"
image: "img/stared.jpg"
date:   2018-03-24 1:00:00
---

长按下载吧😆

++++++++++ ++++++++++

脑图欣赏

++++++++++ ++++++++++

设计模式

<div class="scale"><img src="img/resources/DesignPatterns.png"  alt="设计模式" /></div>

设计模式之间的关系

<div class="scale"><img src="img/resources/the-relationship-between-design-patterns.jpg"  alt="设计模式之间的关系" /></div>

J2EE模式

<div class="scale"><img src="img/resources/J2EEPatterns.png"  alt="J2EE模式" /></div>

架构模式

<div class="scale"><img src="img/resources/ArchitecturalPatterns.png"  alt="架构模式" /></div>

++++++++++ ++++++++++

设计模式 招式+心法

++++++++++ ++++++++++

五种 创建型模式，这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式。

1) Factory Pattern

Step 01：创建接口，接口抽象出要处理的业务

Step 02：创建实体类，实体类用来实现接口

Step 03：创建工厂，工厂可以基于给定的信息生成实体类的对象

Step 04：使用工厂，通过传递类型信息给工厂，来获取实体类的对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/factory_pattern_uml_diagram.jpg"  alt="Factory Pattern" /></div>

2) Abstract Factory Pattern

Step 01：创建各个工厂的接口，接口抽象出当前工厂要处理的业务

Step 02：创建各个工厂的实体类，实体类用来实现当前工厂接口

Step 03：创建抽象工厂 AbstractFactory，抽象工厂为每个工厂对象创建抽象类来获取每个工厂

Step 04：创建扩展抽象工厂的工厂类，工厂类可以基于给定的信息生成实体类的对象

Step 05：创建工厂创造器/生成器类 FactoryProducer，通过传递工厂的具体信息来获取工厂

Step 06：使用 FactoryProducer 来获取 AbstractFactory，通过传递类型信息来获取实体类的对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/abstractfactory_pattern_uml_diagram.jpg"  alt="Abstract Factory Pattern" /></div>

3）Singleton Pattern

Step 01：创建singleton类 SingleObject

Step 02：从singleton类获取唯一的对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/singleton_pattern_uml_diagram.jpg"  alt="Singleton Pattern" /></div>

4）Builder Pattern

Step 01：创建接口，包括表示条目 item 和组装 packing 的接口

Step 02：创建实体类，实体类实现 packing 接口

Step 03：创建实现 item 接口的抽象类，抽象类提供了默认功能

Step 04：创建扩展抽象类的实体类

Step 05：创建包含带有 item的Object 类

Step 06：创建 ObjectBuilder 类，实际的 builder 类负责创建 Object 对象

Step 07：使用 ObjectBuilder 创建对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/builder_pattern_uml_diagram.jpg"  alt="Builder Pattern" /></div>

5）Prototype Pattern

Step 01：创建是想Clonable接口的抽象类 AbstractObject

Step 02：创建扩展抽象类的实体类 Object

Step 03：创建类 ObjectCache，从数据库获取实体类，并存储在Hashtable里

Step 04：使用 ObjectCache 类 来获取存储在Hashtable中的对象的克隆

<div class="scale"><img src="img/resources/DesignPatternDiagrams/prototype_pattern_uml_diagram.jpg"  alt="Prototype Pattern" /></div>

结构型模式，这些设计模式关注类和对象的组合。

Adapter Pattern

Bridge Pattern

Filter Pattern

行为型模式，这些设计模式关注对象之间的通信。
