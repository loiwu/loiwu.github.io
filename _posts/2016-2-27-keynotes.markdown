---
layout: post
title:  "iOS 研发积累"
date:   2016-2-27 9:15:00 +0800
published:  true
categories: my projects
---

我从事iOS研发工作已有三年光景，想以Q&A的形式浅谈在iOS开发的积累，问出问题，给出回答思路。我参考了一些前辈的传道授业解惑。

这些问题从以下角度出发：
1. C语言
2. Objective-C
3. iOS开发
4. Swift

------

**C语言**

Q：怎样在Mac OS X中创建一个C项目？
A：
Xcode中选择命令行程序，并使用C语言

Q：C程序的运行的过程是怎样的？
A：
分为编译和运行两步；
编译前会进行预处理，编译同时进行语法检查，.c文件在编译成功后生成.obj文件；
所有.obj和C语言函数库经过成功链接生成一个可执行文件

Q：C语言的数据类型有哪些？
A：
基本类型 - 整形int、浮点型（单精度float、双精度double）、字符型char；
构造类型 - 数组、结构体struct、枚举enum、共用体union；
指针类型 - void *；
空类型 - void

Q：C语言的类型修饰符有哪些？
A：
short短型、long长型、signed有符号型、unsigned无符号型

Q：C语言中常用的格式符有哪些？
A：
%d、%u、%o、%x、%c、%s、%f、%e
格式费用%前的正数可设置前段补齐，负数可设置后端对齐；
小数点后的整数控制小数点后保留的小数位数

Q：什么是C语言指针？
A：
存放变量地址的变量；
直接引用和间接引用

Q：请写一个函数，实现小写字母转换成大写字母
A：
ASCII、指针移动

Q：什么是函数指针？写一段程序说明它的应用 ☆
A：
？

Q：C语言中有哪些常用的预处理命令？
A：
宏定义、条件编译、文件包含

Q：C语言变量的作用范围有哪些？
A：
全局变量、局部变量

Q：C语言变量的存储位置有哪些，分别对应着怎样的变量存储方式？☆
A：
普通内存（静态存储区）、运行时堆栈（动态存储区）、硬件寄存器（动态存储区）；
静态变量、自动变量、寄存器变量

Q：C语言中控制可访问性的关键字有哪些？
A：
extern、static

Q：C语言中的构造类型有哪些？举例说明它们的不同之处
A：
结构体struct、枚举enum、共用体union

Q：什么事“内存对齐”？
A：
最终参照值为对齐参数和数据长度的最小值；
偏移量必须是最终参照值的整数倍，如果不是就需要进行补齐

**Objective-C**

Q：Objective-C语言的属性生成规则是怎样的？
A：
声明属性、属性与成员变量的关系；
setter和getter方法；
@synthesize实现；

Q：Objective-C语言中self指针是什么？
A：
self代表调用的类；
self代表当前方法的调用者

Q：自定义构造方法使用时需要手动申请内存，怎样处理代码可以更精简？
A：
通过定义一个静态方法嵌套住自定义构造方法

Q：怎么理解KVC？
A：
利用字符串方式动态控制一个对象，对属性进行动态读写；
NSKeyValueCoding协议：
    *动态设置： setValue:属性值 forKey:属性名、setValue:属性值 forKeyPath:属性路径；
    *动态读取： valueForKey:属性名 、valueForKeyPath:属性名

Q：怎么理解KVC？举一个KVC的应用实例？☆
A：
KVO是一种观察者模式，利用它易于实现视图组件和数据模型的分离，当数据模型的属性值改变后，作为监听器的视图组件就会被激发，激发时就会回调监听器自身；
KVO操作常用的方法：
    *注册指定Key路径的监听器： addObserver: forKeyPath: options:  context:
    *删除指定Key路径的监听器： removeObserver: forKeyPath、removeObserver: forKeyPath: context:
    *回调监听： observeValueForKeyPath: ofObject: change: context:
KVO的使用步骤：
    *通过addObserver:forKeyPath:options:context:为被监听对象（通常是数据模型）注册监听器
    *重写监听器的observeValueForKeyPath:ofObject:change:context:方法
应用实例：
给人员分配账户时，给账户的balance属性添加监听，在监听回调方法中输出监听到的信息，同时在对象销毁时移除监听。

Q：Foundation框架中有哪些常用的结构体？
A：
NSRange、NSPoint、NSSize、NSRect;
NSPoint - CGPoint, NSSize - CGSIze, NSRect - CGRect;
对于常用结构体，在Foundation框架中都有一个对应的Make方法进行创建，与之对应的还有一个NSStringFromXX方法进行字符串装换

Q：Objective-C中常见的字符串操作有哪些？
A：
不可变字符串，初始化、大小写转化、后缀前缀判断、字符串比较、字符串截取、字符串转换
可变字符串，设置、追加、替换、插入、删除

Q：Objective-C中国的文件操作有哪些内容？
A：
在Objective-C中，路径、文件读写等操作是利用字符串完成的；
读取文件内容，stringWithContentsOfFile:encoding:error:；
通过URL读取本地或网络文件，stringWithCOntentsOfURL:encoding:error:
写入文件，writeToFile:atomically:encoding:error:

Q：NSArray使用中的注意点有哪些？
A：
NSArray中只能存放对象，不能存放基本数据类型，通常我们可以通过在基本数据类型前加@进行转换；
数组中的元素后面必须加nil以表示数据结束；
makeObjectsPerformSelector执行数组中对象的方法，其参数最多只能有一个；
上面数组操作中无论是数组的追加、删除、截取都没有改变原来的数组，只是产生了新的数组而已；
对象的比较除了使用系统自带的方法，我们可以通过自定义比较器的方法来实现；

Q：NSMutableArray使用中的注意点有哪些？
A：
可变数组中的元素后面必须加nil以表示数据结束；
往一个可变数组中添加一个对象，此时这个对象的引用计数器会加1，当这个对象从可变数组中移除其引用计数器减1。同时当整个数组销毁之后会依次调用每个对象的releaes方法。
在不可变数组中无论对数组怎么排序，原来的数组顺序都不会改变，但是在可变数组中如果使用sortUsingSelector:排序原来的数组顺序就发生了变化。

Q：NSNull的使用时怎样的？
A：
[NSNull null]，NSNull是一个单例，只有一个null方法

Q：@在Objective-C中的用途？
A：
关键字前加@，字符串前使用@，%@表示输出一个对象，@表示装箱

Q：Objective-C中如何实现反射操作？
A：
isKindOfClass:[NSObject class] //判断一个对象是否为某种类型（如果是父类也返回YES）；
isMemberOfClass:[NSObject class] //判断一个对象是否是某个类的实例化对象；
conformsToProtocol:@protocol(NSCopying) //是否实现了某个协议；
respondsToSelector:@selector(showMessage:) //是否存在某个方法；
performSelector:@selector(showMessage:) withObject:@"Hello,world!"]; //动态调用一个方法，注意如果有参数那么参数类型只能为ObjC对象，并且最多只能有两个参数；
//动态生成一个类
Class myClass=NSClassFromString(className);//根据类名生成类；
//类转化为字符串
NSStringFromClass(myClass)；
//调用方法
SEL mySelector=NSSelectorFromString(methodName);
[person3 performSelector:mySelector withObject:@"Hello,world!"];

Q：什么是浅复制？什么是深复制？
A：
指针复制、内容复制；
完全复制；
可变对象、不可变对象

Q：retain、copy、mutableCopy对应的深浅复制是怎样的？
A：
浅浅、浅深、深深

Q：Foundation中的文件操作是怎样的？
A：
[NSFileManager defaultManager]; 


