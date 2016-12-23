---
layout: post
title:  "iOS Architecture Patterns"
date:   2016-12-6 7:17:00 +0800
published:  false
categories: bbkit
---


>关键词：MVC、MVP、MVVM、VIPER

>参考：

- [Apple’s MVC](https://developer.apple.com/library/content/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html)
- [single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle)
- [Average App Store Review Times](http://appreviewtimes.com/)
- [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
- [MVP](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter)
- [MVVM](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)
- [VIPER](https://www.objc.io/issues/13-architecture/viper/)
- [data access layer](https://en.wikipedia.org/wiki/Data_access_layer)
- [view controller offloading](https://www.objc.io/issues/1-view-controllers/lighter-view-controllers/)
- [Unit Testing](http://nshipster.com/unit-testing/)
- [What's worth unit testing in objective-c](http://ashfurrow.com/blog/whats-worth-unit-testing-in-objective-c/)
- [functional reactive programming](https://en.wikipedia.org/wiki/Functional_reactive_programming)

>好的架构

- 每一个实体都有自己严格的角色划分，角色的负担的职责很均衡
- 可测，尤其是可以Unit Test
- 好开发，并且易维护

>MV(X)

- 三大分类：
1）Models：数据的接入层
2）Views：GUI界面
3）Controller/Presenter/ViewModel：Model和View的粘合剂或中介者。当Model改变时更新View，根据View上的行为改变Model
- 区分三大角色，帮助可以帮助开发者更好的理解各种划分，合理重用，独立测试

>MVC

- 传统的MVC：当Model改变时View会通过Controller重新渲染。
- Apple的MVC：Controller是Model和View的中介者，Modle和View彼此隔离

>MVP

- 被动视图(Passive View)

>MVVM

- MVVM将controller视为View
- View和Model间没有强耦合
- View Model独立了View和View的状态
- ViewModel主动改变Model，ViewModel通过更新Model来更新自身。View和ViewModel绑定在一起，可以相互更新

- 绑定方式：KVO式、函数响应式
