---
layout: post
title:  "网络开发"
date:   2016-3-1 9:15:00 +0800
published:  true
categories: my projects
---

我将会从以下四方面讨论网络开发在XXSDK项目中的应用情况：

1. Web请求和响应
2. NSURLSession
3. UIWebView
4. 网络状态

**Web请求和响应**

发送request：
urlStr，编码NSUTF8StringEncoding，url，创建NSMutableURLRequest、设置请求setHTTPMethod:@"POST"、准备需要发送的string、编码成NSData、设置request体setHTTPBody:bodyData、发送request

NSURLConnection
+ (void)sendAsynchronousRequest:request: queue:queue:completionHandler:发送一个异步请求
+ (NSData *)sendSynchronousRequest: returningResponse: error:发送一个同步请求 

NSError *error;
//将对象序列化为字典
NSDictionary *dic= [NSJSONSerialization JSONObjectWithData:data options:0 error:&error];
//将对象反序列化为data
NSData *data = [NSJSONSerialization dataWithJSONObject:dic options:0 error:&error]];

图片缓存：SDWebImage
缓存文件是否过期，缓存文件原来越大如何管理
- (void)sd_setImageWithURL:(NSURL *)url placeholderImage:(UIImage *)placeholder completed:(SDWebImageCompletionBlock)completedBlock;


文件下载：

#pragma mark 异步下载文件

#pragma mark  取得文件大小
NSMutableURLRequest requestWithURL:cachePolicy:timeoutInterval:
setHTTPMethod:@"HEAD"
NSURLConnection sendSynchronousRequest:returningResponse:error:
response.expectedContentLength

#pragma mark 下载指定块大小的数据
//通过请求头设置数据请求范围
[request setValue:range forHTTPHeaderField:@"Range"];

#pragma mark 文件追加
//以可写方式打开文件
NSFileHandle *fileHandle=[NSFileHandle fileHandleForWritingAtPath:filePath];
//如果存在文件则追加，否则创建
if (fileHandle) {
    [fileHandle seekToEndOfFile];
    [fileHandle writeData:data];
    [fileHandle closeFile];//关闭文件
}else{
    [data writeToFile:filePath atomically:YES];//创建文件
}

#pragma mark 取得请求链接 - 一个url
stringByAddingPercentEscapesUsingEncoding:

#pragma mark 取得保存地址(保存在沙盒缓存目录)
[NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES) lastObject];

文件上传：

上传请求头组成：
Content-Length:111
Content-Type:multipart/form-data; charset=%@; boundary=%@

上传请求体组成：
--boundary
Content-Disposition:form-data;name=”表单控件名称”;filename=”上传文件名称”
Content-Type:文件MIME Types
文件二进制数据;
--boundary--

**NSURLSession**

NSURLSession提供了配置会话缓存、协议、cookie和证书能力，这使得网络架构和应用程序可以独立工作、互不干扰。

NSURLConnection完成的三个主要任务：获取数据（通常是JSON、XML等）、文件上传、文件下载。其实在NSURLSession时代，他们分别由三个任务来完成：NSURLSessionDataTask、NSURLSessionUploadTask、NSURLSessionDownloadTask，这三个类都是NSURLSessionTask这个抽象类的子类，相比直接使用NSURLConnection,NSURLSessionTask支持任务的暂停、取消和恢复，并且默认任务运行在其他非主线程中

数据请求：NSURLSessionDataTask
//1.创建url
//2.创建请求
//3.创建会话（这里使用了一个全局会话）并且启动任务
//从会话创建任务
//恢复线程，启动任务

数据上传：NSURLSessionUploadTask
//1.创建url
//2.创建请求
//3.构建数据
[request setValue:[NSString stringWithFormat:@"%lu",(unsigned long)data.length] forHTTPHeaderField:@"Content-Length"];
[request setValue:[NSString stringWithFormat:@"multipart/form-data; boundary=%@",@"KenshinCui"] forHTTPHeaderField:@"Content-Type"];
//4.创建会话

文件下载：NSURLSessionDownloadTask
//1.创建url
//2.创建请求
//3.创建会话（这里使用了一个全局会话）并且启动任务
 NSURLSessionDownloadTask *downloadTask=[session downloadTaskWithRequest:request completionHandler:^(NSURL *location, NSURLResponse *response, NSError *error) {}];
//注意location是下载后的临时保存路径,需要将它移动到需要保存的位置
NSURL *saveUrl=[NSURL fileURLWithPath:savePath];
[[NSFileManager defaultManager] copyItemAtURL:location toURL:saveUrl error:&saveError];

NSURLSessionDownloadDelegate：
-(void)URLSession:(NSURLSession *)session downloadTask:(NSURLSessionDownloadTask *)downloadTask didWriteData:(int64_t)bytesWritten totalBytesWritten:(int64_t)totalBytesWritten totalBytesExpectedToWrite:(int64_t)totalBytesExpectedToWrite;
-(void)URLSession:(NSURLSession *)session downloadTask:(NSURLSessionDownloadTask *)downloadTask didFinishDownloadingToURL:(NSURL *)location;
-(void)URLSession:(NSURLSession *)session task:(NSURLSessionTask *)task didCompleteWithError:(NSError *)error;

后台下载：
#pragma mark 取得一个后台会话(保证一个后台会话，这通常很有必要)
NSURLSessionConfiguration *sessionConfig=[NSURLSessionConfiguration backgroundSessionConfigurationWithIdentifier:@"com.cmjstudio.URLSession"];
//创建会话
session=[NSURLSession sessionWithConfiguration:sessionConfig delegate:self delegateQueue:nil];//指定配置和代理

长时间任务下载完成，更新UI：
-(void)application:(UIApplication *)application handleEventsForBackgroundURLSession:(NSString *)identifier completionHandler:(void (^)())completionHandler
-(void)URLSessionDidFinishEventsForBackgroundURLSession:(NSURLSession *)session{
AppDelegate *appDelegate = (AppDelegate *)[[UIApplication sharedApplication] delegate];}

**UIWebView**

//创建请求
NSURLRequest *request=[NSURLRequest requestWithURL:url];
//加载请求页面
[_webView loadRequest:request];
UIWebView内容加载事件同样是通过代理通知外界，常用的代理方法如开始加载、加载完成、加载出错等，这些方法通常可以帮助开发者更好的控制请求加载过程。

UIWebView与页面交互:

stringByEvaluatingJavaScriptFromString:
[_webView stringByEvaluatingJavaScriptFromString:@"document.title"];
[_webView stringByEvaluatingJavaScriptFromString:@"document.getElementById('header').innerHTML='Kenshin Cui\\'s Blog'"];

页面中的js是无法直接调用ObjC方法的，但是可以变换一下思路：当需要进行一个js操作时让页面进行一个重定向，并且在重定向过程中传入一系列参数。在UIWebView的代理方法中有一个webView: shouldStartLoadWithRequest:navigationType方法，这个方法会在页面加载前执行，这样可以在这里拦截重定向，并且获取定向URL中的参数，根据这些参数约定一个方法去执行。


**网络状态**
Reachability
使用AFNetworking框架检测网络状态：

#pragma mark 网络状态监测
-(void)checkNetworkStatus{
    //创建一个用于测试的url
    NSURL *url=[NSURL URLWithString:@"http://www.apple.com"];
    AFHTTPRequestOperationManager *operationManager=[[AFHTTPRequestOperationManager alloc]initWithBaseURL:url];
    //根据不同的网络状态改变去做相应处理
    [operationManager.reachabilityManager setReachabilityStatusChangeBlock:^(AFNetworkReachabilityStatus status) {
        switch (status) {
            case AFNetworkReachabilityStatusReachableViaWWAN:
                [self alert:@"2G/3G/4G Connection."];
            break;
            case AFNetworkReachabilityStatusReachableViaWiFi:
                [self alert:@"WiFi Connection."];
            break;
            case AFNetworkReachabilityStatusNotReachable:
                [self alert:@"Network not found."];
            break;

            default:
                [self alert:@"Unknown."];
            break;
        }
    }];
    //开始监控
    [operationManager.reachabilityManager startMonitoring];
}
