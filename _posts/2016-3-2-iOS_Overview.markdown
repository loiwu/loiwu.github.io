---
layout: post
title:  "iOS开发概览"
date:   2016-3-1 9:15:00 +0800
published:  true
categories: my projects
---

**程序运行的过程**

main函数进入消息循环UIApplicationMain
UIApplicationMain方法根据第三个参数创建对应UIApplication对象，
该对象根据第四个参数AppDelegate创建并指定UIApplication的代理；
UIApplication开启消息循环监听程序活动，当程序生命周期发生改变时，UIApplication会调用相应的代理方法。

**UITableview**

对于单行文本数据的显示调用- (CGSize)sizeWithAttributes:(NSDictionary *)attrs;方法来得到文本宽度和高度。
对于多行文本数据的显示调用- (CGRect)boundingRectWithSize:(CGSize)size options:(NSStringDrawingOptions)options attributes:(NSDictionary *)attributes context:(NSStringDrawingContext *)context ;方法来得到文本宽度和高度；同时注意在此之前需要设置文本控件的numberOfLines属性为0。
通常我们会在自定义Cell中设置一个高度属性，用于外界方法调用，因为Cell内部设置Cell的高度是没有用的，UITableViewCell在初始化时会重新设置高度。
Cell的高度需要重新设置（前面说过无论Cell内部设置多高都没有用，需要重新设置），这里采用的方法是首先创建对应的Cell，然后在- (CGFloat)tableView:(UITableView *)tableView heightForRowAtIndexPath:(NSIndexPath *)indexPath;方法中设置微博数据计算高度通知UITableView。

[_tableView setEditing:!_tableView.isEditing animated:true];
-(void)tableView:(UITableView *)tableView commitEditingStyle:(UITableViewCellEditingStyle)editingStyle forRowAtIndexPath:(NSIndexPath *)indexPath;
[tableView deleteRowsAtIndexPaths:@[indexPath] withRowAnimation:UITableViewRowAnimationBottom];
[tableView insertRowsAtIndexPaths:@[indexPath] withRowAnimation:UITableViewRowAnimationBottom];
-(void)tableView:(UITableView *)tableView moveRowAtIndexPath:(NSIndexPath *)sourceIndexPath toIndexPath:(NSIndexPath *)destinationIndexPath;
-(UITableViewCellEditingStyle)tableView:(UITableView *)tableView editingStyleForRowAtIndexPath:(NSIndexPath *)indexPath;

UITableView的刷新方法:
- (void)reloadData;刷新整个表格。
- (void)reloadRowsAtIndexPaths:(NSArray *)indexPaths withRowAnimation:(UITableViewRowAnimation)animation NS_AVAILABLE_IOS(3_0);刷新指定的分组和行。
- (void)reloadSections:(NSIndexSet *)sections withRowAnimation:(UITableViewRowAnimation)animation NS_AVAILABLE_IOS(3_0);刷新指定的分组。
- (void)deleteRowsAtIndexPaths:(NSArray *)indexPaths withRowAnimation:(UITableViewRowAnimation)animation;删除时刷新指定的行数据。
- (void)insertRowsAtIndexPaths:(NSArray *)indexPaths withRowAnimation:(UITableViewRowAnimation)animation;添加时刷新指定的行数据。

**视图切换**
tabBarController.viewControllers=@[webChatController,contactController];
//注意默认情况下UITabBarController在加载子视图时是懒加载的，所以这里调用一次contactController，否则在第一次展示时只有第一个控制器tab图标，contactController的tab图标不会显示
for (UIViewController *controller in tabBarController.viewControllers) {
UIViewController *view= controller.view;
}
_window.rootViewController=tabBarController;
[_window makeKeyAndVisible];

Segue的工作方式分为以下几个步骤：
1.创建目标视图控制器（也就是前面的General、Sounds视图控制器）
2.创建Segue对象
3.调用源视图对象的prepareForSegue:sender:方法
4.调用Segue对象的perform方法将目标视图控制器推送到屏幕
5.释放Segue对象

在iOS开发中常用的参数传递有以下几种方法：
1. 采用代理模式
2. 采用iOS消息机制
3. 通过NSDefault存储（或者文件、数据库存储等）
4. 通过AppDelegate定义全局变量（或者使用UIApplication、定义一个单例类等）
5. 通过控制器属性传递

在iOS中事件分为三类：
1. 触摸事件：通过触摸、手势进行触发（例如手指点击、缩放）
2. 运动事件：通过加速器进行触发（例如手机晃动）
3. 远程控制事件：通过其他远程设备触发（例如耳机控制按钮）

UITouch
window：触摸时所在的窗口
view：触摸时所在视图
tapCount:短时间内点击的次数
timestamp:触摸产生或变化的时间戳
phase:触摸周期内的各个状态
locationInView:方法：取得在指定视图的位置
previousLocationInView:方法：取得移动的前一个位置


事件处理机制

在iOS中发生触摸后，事件会加入到UIApplication事件队列（在这个系列关于iOS开发的第一篇文章中我们分析iOS程序原理的时候就说过程序运行后UIApplication会循环监听用户操作），UIApplication会从事件队列取出最前面的事件并分发处理，通常先分发给应用程序主窗口，主窗口会调用hitTest:withEvent:方法（假设称为方法A，注意这是UIView的方法），查找合适的事件触发视图（这里通常称为“hit-test view”）：

在顶级视图（key window的视图）上调用pointInside:withEvent:方法判断触摸点是否在当前视图内；
如果返回NO，那么A返回nil；
如果返回YES，那么它会向当前视图的所有子视图（key window的子视图）发送hitTest:withEvent:消息，遍历所有子视图的顺序是从subviews数组的末尾向前遍历（从界面最上方开始向下遍历）。
如果有subview的hitTest:withEvent:返回非空对象则A返回此对象，处理结束（注意这个过程，子视图也是根据pointInside:withEvent:的返回值来确定是返回空还是当前子视图对象的。并且这个过程中如果子视图的hidden=YES、userInteractionEnabled=NO或者alpha小于0.1都会并忽略）；
如果所有subview遍历结束仍然没有返回非空对象，则A返回顶级视图；


在iOS中添加手势比较简单，可以归纳为以下几个步骤：
1. 创建对应的手势对象；
2. 设置手势识别属性【可选】；
3. 附加手势到指定的对象；
4. 编写手势操作方法；

创建一个本地通知通常分为以下几个步骤：
1. 创建UILocalNotification。
2. 设置处理通知的时间fireDate。
3. 配置通知的内容：通知主体、通知声音、图标数字等。
4. 配置通知传递的自定义数据参数userInfo（这一步可选）。
5. 调用通知，可以使用scheduleLocalNotification:按计划调度一个通知，也可以使用presentLocalNotificationNow立即调用通知。

