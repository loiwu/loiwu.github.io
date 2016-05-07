---
layout: post
title:  "多线程"
date:   2016-3-1 9:15:00 +0800
published:  true
categories: my projects
---

我将会从以下四方面讨论多线程开发在XXSDK项目中的应用情况：

1. NSThread
2. NSOperation
3. GCD
4. 线程同步

**NSThread**

轻量级多线程开发NSThread，解决线程阻塞，实现多线程并发，控制线程状态

用法：直接将操作添加到线程中并启动
+ (void)detachNewThreadSelector:(SEL)selector toTarget:(id)target withObject:(id)argument
例子：
当任务执行时，展示进程显示控件ProgressHUD
[NSThread detachNewTHreadSelector:selector(launchExecution) toTarget:self withObject:nil];

用法：创建一个线程对象，然后调用start启动线程
- (instancetype)initWithTarget:(id)target selector:(SEL)selector object:(id)argument 
例子：
不是在主线程上发送request
_networkRequestThread = [[NSThread alloc] initWithTarget:self selector:@selector(networkRequestThreadEntryPoint:) object:nil];
[_networkRequestThread start];

用法：回到主线程进行操作
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait;
例子：
回到主线程，控制网络活动指示器的显示
[[self class] performSelectorOnMainThread:@selector(hideNetworkActivityIndicatorAfterDelay) withObject:nil waitUntilDone:[NSThread isMainThread]];

用法：获取和控制线程状态
//让当前线程休眠一段时间
[NSThread sleepForTimeInterval:sleepDuration];
//获得当前线程
[NSThread currentThread];
//设置线程为取消状态
[thread cancel];
//取消当前线程
[NSThread exit];

用法：利用NSObject的分类扩展方法进行多线程开发
- (void)performSelectorInBackground:(SEL)aSelector withObject:(id)arg：在后台执行一个操作，本质就是重新创建一个线程执行当前方法。
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thr withObject:(id)arg waitUntilDone:(BOOL)wait：在指定的线程上执行一个方法，需要用户创建一个线程对象。
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait：在主线程上执行一个方法。

**NSOperation**

将NSOperation放到NSOperationQueue这个队列中线程就会依次启动。NSOperationQueue负责管理、执行所有的NSOperation，在这个过程中可以更加容易的管理线程总数和控制线程之间的依赖关系。
NSOperation有两个常用子类用于创建线程操作：NSInvocationOperation和NSBlockOperation，两种方式本质没有区别，但是是后者使用Block形式进行代码组织，使用相对方便。

用法：NSInvocationOperation 创建一个操作，在这个操作中指定调用方法和参数，然后加入到操作队列。
- (nullable instancetype)initWithTarget:(id)target selector:(SEL)sel object:(nullable id)arg;
例子：
NSInvocationOperation *invocationOperation = [[NSInvocationOperation alloc]initWithTarget:self selector:@selector(loadImage) object:nil];
NSOperationQueue *operationQueue=[[NSOperationQueue alloc]init];
[operationQueue addOperation:invocationOperation];

用法：NSBlockOperation
例子：
[[NSOperationQueue mainQueue] addOperationWithBlock:^{
    [self updateImageWithData:data andIndex:i];
}];

用法：线程执行顺序控制
例子：
-(void)loadImageWithMultiThread{
    int count=ROW_COUNT*COLUMN_COUNT;
//创建操作队列
    NSOperationQueue *operationQueue=[[NSOperationQueue alloc]init];
        operationQueue.maxConcurrentOperationCount=5;//设置最大并发线程数
    NSBlockOperation *lastBlockOperation=[NSBlockOperation blockOperationWithBlock:^{
        [self loadImage:[NSNumber numberWithInt:(count-1)]];
    }];
//创建多个线程用于填充图片
    for (int i=0; i<count-1; ++i) {
        //方法1：创建操作块添加到队列
        //创建多线程操作
        NSBlockOperation *blockOperation=[NSBlockOperation blockOperationWithBlock:^{
            [self loadImage:[NSNumber numberWithInt:i]];
        }];
        //设置依赖操作为最后一张图片加载操作
        [blockOperation addDependency:lastBlockOperation];
        [operationQueue addOperation:blockOperation];
    }
        //将最后一个图片的加载操作加入线程队列
    [operationQueue addOperation:lastBlockOperation];
}

**GCD**

例1：
dispatch_queue_t mainQueue = dispatch_get_main_queue();
dispatch_sync(mainQueue, ^{
    [self updateImageWithData:data andIndex:i];
});

例2：
dispatch_queue_t serialQueue = dispatch_queue_create("myThreadQueue1", DISPATCH_QUEUE_SERIAL);//注意queue对象不是指针类型
for (int i=0; i<count; ++i) {
    //异步执行队列任务
    dispatch_async(serialQueue, ^{
        [self loadImage:[NSNumber numberWithInt:i]];
    });
}
//非ARC环境请释放
    dispatch_release(seriQueue);

例3：
static dispatch_queue_t http_request_operation_processing_queue() {
    static dispatch_queue_t tr_http_request_operation_processing_queue;
    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        tr_http_request_operation_processing_queue = dispatch_queue_create("com.teiron.http-request.processing", DISPATCH_QUEUE_CONCURRENT);
    });
    return tr_http_request_operation_processing_queue;
}

例4：
dispatch_queue_t globalQueue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
dispatch_sync(dispatch_queue_t queue, dispatch_block_t block);
dispatch_async(dispatch_queue_t queue, dispatch_block_t block);

用法：GCD执行任务的方法
dispatch_async()异步调用。
dispatch_sync()同步调用。
dispatch_apply():重复执行某个任务。
dispatch_once():单次执行一个任务。

例子：dispatch_time()：延迟一定的时间后执行。
if (self.isPackUping || self.isStretching) {
    dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(1 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
    [self updateMenuItem:array];
    });
}

用法：
dispatch_barrier_async()：使用此方法创建的任务首先会查看队列中有没有别的任务要执行，如果有，则会等待已有任务执行完毕再执行；同时在此方法后添加的任务必须等待此方法中任务执行后才能执行。（利用这个方法可以控制执行顺序）
例子：SDWebImage
- (id)initWithRequest:(NSURLRequest *)request
            options:(SDWebImageDownloaderOptions)options
            progress:(SDWebImageDownloaderProgressBlock)progressBlock
            completed:(SDWebImageDownloaderCompletedBlock)completedBlock
            cancelled:(SDWebImageNoParamsBlock)cancelBlock;‘
取消块中：
dispatch_barrier_async(sself.barrierQueue, ^{
    [sself.URLCallbacks removeObjectForKey:url];
});

用法：dispatch_group_async()：实现对任务分组管理
dispatch_queue_t queue = strongOperation.successCallbackQueue ?: dispatch_get_main_queue();
#pragma clang diagnostic pop
dispatch_group_async(dispatchGroup, queue, ^{
    if (originalCompletionBlock) {
        originalCompletionBlock();
    }
    NSUInteger numberOfFinishedOperations = [[operations indexesOfObjectsPassingTest:^BOOL(id op, NSUInteger __unused idx,  BOOL __unused *stop) {
        return [op isFinished];
    }] count];
    if (progressBlock) {
        progressBlock(numberOfFinishedOperations, [operations count]);
    }
    dispatch_group_leave(dispatchGroup);
});

用法：一组任务全部完成可以通过dispatch_group_notify()方法获得完成通知（需要定义dispatch_group_t作为分组标识）
例子：AFNetworking
__block dispatch_group_t dispatchGroup = dispatch_group_create();
NSBlockOperation *batchedOperation = [NSBlockOperation blockOperationWithBlock:^{
    dispatch_group_notify(dispatchGroup, dispatch_get_main_queue(), ^{
        if (completionBlock) {
            completionBlock(operations);
        }
    });
#if !OS_OBJECT_USE_OBJC
    dispatch_release(dispatchGroup);
#endif
}];

**线程同步**

”加锁代码“应该是抢占资源的读取和修改代码

用法：NSLock、tryLock、lockBeforeData:
例子：
//加锁
[_lock lock];
//使用完解锁
[_lock unlock];

用法：@synchronized代码块
首先选择一个对象作为同步对象（一般使用self），然后将”加锁代码”（争夺资源的读取、修改代码）放到代码块中。
@synchronized中的代码执行时先检查同步对象是否被另一个线程占用，如果占用该线程就会处于等待状态，直到同步对象被释放。


总结

1>无论使用哪种方法进行多线程开发，每个线程启动后并不一定立即执行相应的操作，具体什么时候由系统调度（CPU空闲时就会执行）。

2>更新UI应该在主线程（UI线程）中进行，并且推荐使用同步调用，常用的方法如下：

- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait (或者-(void)performSelector:(SEL)aSelector onThread:(NSThread *)thr withObject:(id)arg waitUntilDone:(BOOL) wait;方法传递主线程[NSThread mainThread])
[NSOperationQueue mainQueue] addOperationWithBlock:
dispatch_sync(dispatch_get_main_queue(), ^{}) 

3>NSThread适合轻量级多线程开发，控制线程顺序比较难，同时线程总数无法控制（每次创建并不能重用之前的线程，只能创建一个新的线程）。

4>对于简单的多线程开发建议使用NSObject的扩展方法完成，而不必使用NSThread。

5>可以使用NSThread的currentThread方法取得当前线程，使用 sleepForTimeInterval:方法让当前线程休眠。

6>NSOperation进行多线程开发可以控制线程总数及线程依赖关系。

7>创建一个NSOperation不应该直接调用start方法（如果直接start则会在主线程中调用）而是应该放到NSOperationQueue中启动。

8>相比NSInvocationOperation推荐使用NSBlockOperation，代码简单，同时由于闭包性使它没有传参问题。

9>NSOperation是对GCD面向对象的ObjC封装，但是相比GCD基于C语言开发，效率却更高，建议如果任务之间有依赖关系或者想要监听任务完成状态的情况下优先选择NSOperation否则使用GCD。

10>在GCD中串行队列中的任务被安排到一个单一线程执行（不是主线程），可以方便地控制执行顺序；并发队列在多个线程中执行（前提是使用异步方法），顺序控制相对复杂，但是更高效。

11>在GDC中一个操作是多线程执行还是单线程执行取决于当前队列类型和执行方法，只有队列类型为并行队列并且使用异步方法执行时才能在多个线程中执行（如果是并行队列使用同步方法调用则会在主线程中执行）。

12>相比使用NSLock，@synchronized更加简单，推荐使用后者。
