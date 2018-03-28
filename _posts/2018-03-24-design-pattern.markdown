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

Step 01：创建一个接口

Step 02：创建实现接口的实体类

Step 03：创建一个工厂，生成基于给定信息的实体类的对象

Step 04：使用该工厂，通过传递类型信息来获取实体类的对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/factory_pattern_uml_diagram.jpg"  alt="Factory Pattern" /></div>

2) Abstract Factory Pattern

Step 01：为形状创建一个接口

Step 02：创建实现接口的实体类

Step 03：为颜色创建一个接口

Step 04：创建实现接口的实体类

Step 05：为 Color 和 Shape 对象创建抽象类来获取工厂

Step 06：创建扩展了 AbstractFactory 的工厂类，基于给定的信息生成实体类的对象

Step 07：创建一个工厂创造器/生成器类，通过传递形状或颜色信息来获取工厂

Step 08：使用 FactoryProducer 来获取 AbstractFactory，通过传递类型信息来获取实体类的对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/abstractfactory_pattern_uml_diagram.jpg"  alt="Abstract Factory Pattern" /></div>

3）Singleton Pattern

Step 01：创建一个 Singleton 类

Step 02：从 singleton 类获取唯一的对象

<div class="scale"><img src="img/resources/DesignPatternDiagrams/singleton_pattern_uml_diagram.jpg"  alt="Singleton Pattern" /></div>

4）Builder Pattern

Step 01：创建一个表示食物条目和食物包装的接口

Step 02：创建实现 Packing 接口的实体类

Step 03：创建实现 Item 接口的抽象类，该类提供了默认的功能

Step 04：创建扩展了 Burger 和 ColdDrink 的实体类

Step 05：创建一个 Meal 类，带有上面定义的 Item 对象

Step 06：创建一个 MealBuilder 类，实际的 builder 类负责创建 Meal 对象

Step 07：BuiderPatternDemo 使用 MealBuider 来演示建造者模式（Builder Pattern）

<div class="scale"><img src="img/resources/DesignPatternDiagrams/builder_pattern_uml_diagram.jpg"  alt="Builder Pattern" /></div>

5）Prototype Pattern

Step 01：创建一个实现了 Clonable 接口的抽象类

Step 02：创建扩展了上面抽象类的实体类

Step 03：创建一个类，从数据库获取实体类，并把它们存储在一个 Hashtable 中

Step 04：PrototypePatternDemo 使用 ShapeCache 类来获取存储在 Hashtable 中的形状的克隆

<div class="scale"><img src="img/resources/DesignPatternDiagrams/prototype_pattern_uml_diagram.jpg"  alt="Prototype Pattern" /></div>

结构型模式，这些设计模式关注类和对象的组合。

Adapter Pattern

Step 01：为媒体播放器MediaPlayer和高级媒体播放器AdvancedMediaPlayer创建接口

Step 02：创建实现了 AdvancedMediaPlayer 接口的实体类

Step 03：创建实现了 MediaPlayer 接口的适配器类

Step 04：创建实现了 MediaPlayer 接口的实体类

Step 05：使用 AudioPlayer 来播放不同类型的音频格式

<div><img src="img/resources/DesignPatternDiagrams/adapter_pattern_uml_diagram.jpg" alt="Adapter Pattern"></div>

行为型模式，这些设计模式关注对象之间的通信。
