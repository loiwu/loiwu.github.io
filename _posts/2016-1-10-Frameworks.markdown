---
layout: post
title:  "iOS 那些类"
date:   2016-3-10 12:15:00 +0800
published:  true
categories: my projects
---

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