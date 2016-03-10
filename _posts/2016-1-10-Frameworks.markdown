---
layout: post
title:  "iOS 那些类"
date:   2016-3-10 12:15:00 +0800
published:  true
categories: my projects
---

------

UIKit.framework

------

UIWebView

富媒体容器

    - (void)loadRequest:(NSURLRequest *)request;
    - (void)loadHTMLString:(NSString *)string baseURL:(nullable NSURL *)baseURL;
    - (void)loadData:(NSData *)data MIMEType:(NSString *)MIMEType textEncodingName:(NSString *)textEncodingName baseURL:(NSURL *)baseURL;

// 执行JavaScript方法

    - (nullable NSString *)stringByEvaluatingJavaScriptFromString:(NSString *)script;

UIWebViewDelegate//生命周期代理

    - (BOOL)webView:(UIWebView *)webView shouldStartLoadWithRequest:(NSURLRequest *)request navigationType:(UIWebViewNavigationType)navigationType;
    - (void)webViewDidStartLoad:(UIWebView *)webView;
    - (void)webViewDidFinishLoad:(UIWebView *)webView;
    - (void)webView:(UIWebView *)webView didFailLoadWithError:(nullable NSError *)error;

------

Foundation.framework

------

NSThread

    + (NSThread *)currentThread;
    + (void)detachNewThreadSelector:(SEL)selector toTarget:(id)target withObject:(nullable id)argument;
    - (instancetype)initWithTarget:(id)target selector:(SEL)selector object:(nullable id)argument NS_AVAILABLE(10_5, 2_0);

    - (void)performSelectorOnMainThread:(SEL)aSelector withObject:(nullable id)arg waitUntilDone:(BOOL)wait modes:(nullable NSArray<NSString *> *)array;
    - (void)performSelectorOnMainThread:(SEL)aSelector withObject:(nullable id)arg waitUntilDone:(BOOL)wait;
    - (void)performSelector:(SEL)aSelector onThread:(NSThread *)thr withObject:(nullable id)arg waitUntilDone:(BOOL)wait modes:(nullable NSArray<NSString *> *)array NS_AVAILABLE(10_5, 2_0);
    - (void)performSelector:(SEL)aSelector onThread:(NSThread *)thr withObject:(nullable id)arg waitUntilDone:(BOOL)wait NS_AVAILABLE(10_5, 2_0);
    - (void)performSelectorInBackground:(SEL)aSelector withObject:(nullable id)arg NS_AVAILABLE(10_5, 2_0);

------

NSOperation

    - (void)start;
    - (void)addDependency:(NSOperation *)op;
    - (void)removeDependency:(NSOperation *)op;

NSBlockOperation

    + (instancetype)blockOperationWithBlock:(void (^)(void))block;
    - (void)addExecutionBlock:(void (^)(void))block;

NSInvocationOperation

    - (nullable instancetype)initWithTarget:(id)target selector:(SEL)sel object:(nullable id)arg;
    - (instancetype)initWithInvocation:(NSInvocation *)inv NS_DESIGNATED_INITIALIZER;

NSOperationQueue

    - (void)addOperation:(NSOperation *)op;
    - (void)addOperations:(NSArray<NSOperation *> *)ops waitUntilFinished:(BOOL)wait NS_AVAILABLE(10_6, 4_0);
    - (void)addOperationWithBlock:(void (^)(void))block NS_AVAILABLE(10_6, 4_0);

    - (void)cancelAllOperations;
    - (void)waitUntilAllOperationsAreFinished;
    + (nullable NSOperationQueue *)currentQueue NS_AVAILABLE(10_6, 4_0);
    + (NSOperationQueue *)mainQueue NS_AVAILABLE(10_6, 4_0);

------

NSURL
NSURLRequest
NSURLResponse

------

NSURLSession

NSURLConnection API的替代方案，影响从网络获取NSURLRequest对象的策略以及机制的各个方面。
NSURLSession可以创造NSURLSessionTask对象，代表资源被加载的行为。相比NSURLConnection对象，它提供了更多的控制和更统一的代理模型。

    + (NSURLSession *)sharedSession;

    + (NSURLSession *)sessionWithConfiguration:(NSURLSessionConfiguration *)configuration;
    + (NSURLSession *)sessionWithConfiguration:(NSURLSessionConfiguration *)configuration delegate:(nullable id <NSURLSessionDelegate>)delegate delegateQueue:(nullable NSOperationQueue *)queue;

    - (NSURLSessionDataTask *)dataTaskWithRequest:(NSURLRequest *)request completionHandler:(void (^)(NSData * __nullable data, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;
    - (NSURLSessionDataTask *)dataTaskWithURL:(NSURL *)url completionHandler:(void (^)(NSData * __nullable data, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;
    - (NSURLSessionUploadTask *)uploadTaskWithRequest:(NSURLRequest *)request fromFile:(NSURL *)fileURL completionHandler:(void (^)(NSData * __nullable data, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;
    - (NSURLSessionUploadTask *)uploadTaskWithRequest:(NSURLRequest *)request fromData:(nullable NSData *)bodyData completionHandler:(void (^)(NSData * __nullable data, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;
    - (NSURLSessionDownloadTask *)downloadTaskWithRequest:(NSURLRequest *)request completionHandler:(void (^)(NSURL * __nullable location, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;
    - (NSURLSessionDownloadTask *)downloadTaskWithURL:(NSURL *)url completionHandler:(void (^)(NSURL * __nullable location, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;
    - (NSURLSessionDownloadTask *)downloadTaskWithResumeData:(NSData *)resumeData completionHandler:(void (^)(NSURL * __nullable location, NSURLResponse * __nullable response, NSError * __nullable error))completionHandler;

NSURLSessionDelegate

    - (void)URLSession:(NSURLSession *)session didBecomeInvalidWithError:(nullable NSError *)error;
    - (void)URLSession:(NSURLSession *)session didReceiveChallenge:(NSURLAuthenticationChallenge *)challenge
completionHandler:(void (^)(NSURLSessionAuthChallengeDisposition disposition, NSURLCredential * __nullable credential))completionHandler;
    - (void)URLSessionDidFinishEventsForBackgroundURLSession:(NSURLSession *)session NS_AVAILABLE_IOS(7_0);

NSURLSessionTaskDelegate
NSURLSessionDataDelegate
NSURLSessionDownloadDelegate
NSURLSessionStreamDelegate

------

NSJSONSerialization

将JSON转换为Foundation对象，将Foundation对象转换为JSON的类

//判断一个给定的对象能不能被转换成JSON数据

    + (BOOL)isValidJSONObject:(id)obj;

//从Foundation对象生成JSON数据

    + (nullable NSData *)dataWithJSONObject:(id)obj options:(NSJSONWritingOptions)opt error:(NSError **)error;

//将JSON数据转换成Foundation对象

    + (nullable id)JSONObjectWithData:(NSData *)data options:(NSJSONReadingOptions)opt error:(NSError **)error;

//将JSON对象写成数据流，返回写入数据流的字节数

    + (NSInteger)writeJSONObject:(id)obj toStream:(NSOutputStream *)stream options:(NSJSONWritingOptions)opt error:(NSError **)error;

//通过JSON数据流产生JSON数据

    + (nullable id)JSONObjectWithStream:(NSInputStream *)stream options:(NSJSONReadingOptions)opt error:(NSError **)error;

Summary：

（1）是不是合法的JSON
（2）JSON与Foundation对象互转
（3）JSON与数据流互转

------









------

usr/include

------

<dispatch>

<once.h>

//与dispatch_once()一起使用的断言，必须被初始化为0

    typedef long dispatch_once_t;

//只执行一次block中的逻辑

    void dispatch_once(dispatch_once_t *predicate, dispatch_block_t block);












