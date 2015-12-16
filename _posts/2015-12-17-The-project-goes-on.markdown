---
layout: post
title:  "The Project Goes On"
date:   2015-12-17 12:15:00 +0800
published:  true
categories: my projects
---

#About Project Experience

You can not get everything done, you need help

###About Key Techonology

##About Application Framework

There are five parts for the whole project.

- host environment : SDKDEMO

- static libray : PPAppPlatformKit.framework

- main dynamic libray : PPAppPlatformKitDylib.framework

- sub dynamic libray : PPAppSubDylibPlatformKit.framework

- test libray : PPSDKTestKit.framework

##About terminologies

#[Host Application][null-link]
[null-link]: chrome://not-a-link
Host application is the software environment, all the frameworks work in it.
In the SDK project, the game application is the host application. You can also call it host environment. 

#[Code Libraray][null-link]
[null-link]: chrome://not-a-link
Library supplies a way of code-sharing. There are two kinds of libraries. One is called static library and the other is dynamic library.
In the development iOS area, a static library is in the form of .a or .framework, and a dynamic  library is in the form of .dylib or .framework.

#[Difference between Atatic Library and Dynamic Library][null-link]
The static library is copied to the executable program in link-time. The dynamic library isn't copied to the executable program in link-time. When the program is running, the dynamic library is loaded into memory, and the program can call the dynamic library.

#[About .framework][null-link]
[null-link]: chrome://not-a-link
The .framework supplied by iOS system is the dynamic library, while the .framework supplied by developers themselves is static libray.

#[Difference between .a and .framework][null-link]
[null-link]: chrome://not-a-link
.a and .framework are both the forms of the static library.
The .a file is a pure binary file.
The .framework file does not only include the binary file, but also includes the resource files.
If you want to use the static library which is in the form of .a, you need use in concert with its header files. So we get a formula as follows:
    
    .a + .h + resourceFile = .framework

The static libray in the form of .framework is recommended.

#[Static Libray][null-link]
[null-link]: chrome://not-a-link
As metioned in wikipedia, [the static library](https://en.wikipedia.org/wiki/Static_library) is also called statically-linked library. It's a set of routines, external functions and cariables which are resolved in a caller at compile-time.

In the SDK project, the game application adds PPAppPlatformKit.bundle into the project of itself. PPAppPlatformKit.framework is wrapped into PPAppPlatformKit.bundle. A .plist file which is called pphelper_sdk_Info.plist is also inclued into PPAppPlatformKit.bundle. This plist file contains the important paremeters 
 - SDK_Static_Version : static library string version
 - SDK_Static_Digit_Version : static library digital number version
 - SDK_ChannelCode : channel identifier can help to load diffent UI and functions accroding to different game channels
 - SDK_Sign_Identifier : the signiture of static library can tell sdk whether its target application is a jailbreak version or not.

After the host application set appId and appKey which are supplied by PP developer platform, the game app can call a method named 'startPPSDK'. The work flow of ppsdk static libray starts as follows:

(1)check and update game
(2)check, update and load dynamic library

	main work flow of static library:
	-> <check for update(game)> 
	-> <have update / no update / retry check / quit> 
	->  <check for update(dynamic library)> 
	-> <have update / no update / retry check > 
	-> load dynamic library

The static libary also help host application to connect with the dynamic library. This is the core feature of PPSDK static libary which uses the Objective-C **runtime** mechanism. I will show you the details later.

To be continued ...

#[Main Dynamic Libray][null-link]
[null-link]: chrome://not-a-link

We set 'Per-configuration Build Products Path' in the Build Settings of XCode to control the final location of PPAppPlatformKitDylib.framework after it's built successfully.

#[Sub Dynamic Libray][null-link]
[null-link]: chrome://not-a-link

#[Unit Test Libray][null-link]
[null-link]: chrome://not-a-link











