未完待续  
深切缅怀曾经的文档……    
长期独立开发，没人可交流，视野狭窄，技术缺陷多，被不负责任的blog坑多了就越来越喜欢看官方文档了，日久成喷，而且还发现自己去看英文文档不如去翻别人的blog  
期待你的指导，欢迎在[Issues](https://github.com/saint-shaka/SayGoodByeToiOSDevelopment/issues)里留言！谢谢！  

## <a name='contents'>Table of Contents</a>

  1. [OOP](#OOP)
  1. [OC](#OC)
  1. [Subjects](#Subjects)
  1. [Foundation](#Foundation)
  1. [UI Kit](#UIKit)
  1. [Other](#Other)
  1. [Sigh](#Sigh)
  ### <a name='OOP'> OOP:</a>
  [Object-Oriented Programming with Objective-C](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/OOP_ObjC/Articles/ooWhy.html)
//个人感觉这边很重要，基本是年年看，逐渐加深对每一句话的体会。当年刚开始做的时候，感觉动态加载之类的没用，所以后来……

  ### <a name='OC'> OC:</a>
   [The Objective-C Programming Language](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ObjectiveC/Introduction/introObjectiveC.html#//apple_ref/doc/uid/TP30001163-CH1-SW2)
//没看多久就退役的一本，但是感觉某些地方比下面的那本讲得好，也许是图少了点吧

[Programming with Objective-C](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html)
//做OC必看，包含各种面试题答案和原理，2015年之后的更新就去看网站和WWDC sessions吧

  ### <a name='Subjects'> Subjects:</a>
  [Advanced Memory Management Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/MemoryMgmt/Articles/MemoryMgmt.html#//apple_ref/doc/uid/10000011-SW1)
//内存管理4原则，Autoreleasepool用来降低for的内存峰值，经常被问到吧？

[Transitioning to ARC Release Notes](https://developer.apple.com/library/archive/releasenotes/ObjectiveC/RN-TransitioningToARC/Introduction/Introduction.html#//apple_ref/doc/uid/TP40011226-CH1-SW11)
//用ARC之前被问到有没有用过ARC？用了之后被问到有没有用过MRR？从MRR过渡到ARC的时候真是心惊胆战……

[Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/ios/overview/themes/)
//HIG就是这本，基本年年更新，个人感觉整个团队的都该看看交流交流（不交流交流你怎么知道她看没看）（交流还能增进感情？）(交流交流可以从别人的角度加深理解)（欢迎去issues里留言），看完了再看看自己有没有做过相反设计的东西。当你遇上了自认为不合理的设计，就把这本给那个做设计的，让她看完。

[Coding Guidelines for Cocoa](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html)
//一部分一部分一部分代码规范。既然要出规范，你怎么不写全点呢？是因为我C语言基础太弱吗？

[Start Developing iOS Apps Today](https://developer.apple.com/library/archive/referencelibrary/GettingStarted/RoadMapiOS-Legacy/chapters/Introduction.html)
//不太适合国情的开发路线？

[App Programming Guide for iOS](https://developer.apple.com/library/archive/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007072-CH1-SW1)
//看完了就可以对“App是如何运行的”有个大概的了解

[Threading Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/Introduction/Introduction.html)
//学完操作系统和C再来看这本吧，也是要年年看几遍的，感觉在有人指导的条件下学习比较合适？

[Concurrency Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/ConcurrencyProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008091-CH1-SW1)
//看过好几遍，在我的工作中也没用上多少，但是别人咋就能经常用上呢？配合WWDC sessions看效果更好？

[Timer Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Timers/Timers.html#//apple_ref/doc/uid/10000061-SW1)
//Timers work in conjunction with NSRunLoop objects. As a result, they don’t provide a real-time mechanism—their accuracy is limited.怎么不说如何实现个高精度的timer？这不坑XX吗！

[Cocoa Design Patterns](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaFundamentals/CocoaDesignPatterns/CocoaDesignPatterns.html#//apple_ref/doc/uid/TP40002974-CH6-SW6)
//看完了并没感觉有啥用

[Concepts in Objective-C Programming](https://developer.apple.com/library/archive/documentation/General/Conceptual/CocoaEncyclopedia/Introduction/Introduction.html)
//一些基础面试题的答案就在其中。

[Cocoa Core Competencies](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Introduction.html#//apple_ref/doc/uid/TP40008195-CH68-DontLinkElementID_2)
//基本概念，浅显易懂。

[Information Property List Key Reference](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009248-SW1)
//虽然年年更新，但是很久没看了

[File System Programming Guide](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010672-CH1-SW1)
//Sandbox了解一下。现在仍然有很多地方没看明白，用不上就没再去看

[File System Advanced Programming Topics](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemAdvancedPT/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010765-CH1-SW1)
//内容不多，但是值得储备。谁不接触个读写本地大文件的需求？

[Local and Remote Notification Programming Guide](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/)
//虽说年年更新，但是2014年之后的工作都用的第三方SDK，就再没看过了

[Resource Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/LoadingResources/Introduction/Introduction.html#//apple_ref/doc/uid/10000051i-CH1-SW1)
//看看nib可以加深对xib的认识

[]()
//



### <a name='Foundation'> Foundation:</a>


[Key-Value Coding Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/KeyValueCoding/)
//我怎么就没想到用这个实现自动解析呢？当时还傻不拉几的去做生成手动解析代码……为什么别人看了有用的东西我看了感觉都没啥用呢？

[Key-Value Observing Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/KeyValueObserving/KeyValueObserving.html#//apple_ref/doc/uid/10000177i)
//基本忘光了

[Attributed String Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/AttributedStrings/AttributedStrings.html#//apple_ref/doc/uid/10000036-BBCCGDBG)
//常用，但是应该没多少人看完吧，反正我也是只看了一部分

[Notification Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Notifications/Introduction/introNotifications.html)
//虽然从未用过Delivering Notifications To Particular Threads，但是感觉Coalescing Notifications特别有用

[Date and Time Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DatesAndTimes/DatesAndTimes.html)
//日期这些太常用了

[]()
//

[]()
//
### <a name='UIKit'> UI Kit:</a>

[View Programming Guide for iOS](https://developer.apple.com/library/archive/documentation/WindowsViews/Conceptual/ViewPG_iPhoneOS/Introduction/Introduction.html)
//这还用说？

[View Controller Programming Guide for iOS](https://developer.apple.com/library/archive/featuredarticles/ViewControllerPGforiPhoneOS/index.html#//apple_ref/doc/uid/TP40007457)
//这还用说？

[Table View Programming Guide for iOS](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/TableView_iPhone/AboutTableViewsiPhone/AboutTableViewsiPhone.html)
//这还用说？但是你看过The Elements吗？

[Scroll View Programming Guide for iOS](https://developer.apple.com/library/archive/documentation/WindowsViews/Conceptual/UIScrollView_pg/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008179)
//scrollview的绘制原理不是在这看的？

[Collection View Programming Guide for iOS](https://developer.apple.com/library/archive/documentation/WindowsViews/Conceptual/CollectionViewPGforIOS/Introduction/Introduction.html)
//多用collection view，少用table view吧。（其实我没看完这个）

### <a name='Other'> Other:</a>
[]()
//

[]()
//

### <a name='Sigh'> Sigh:</a>
//连这些都没用过，我都不好意思说我做过iOS开发  
[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007533-SW1)

[Cocoa Drawing Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003290-CH201-SW1)
//
[Core Data Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CoreData/)
//
[Core Text Programming Guide](https://developer.apple.com/library/archive/documentation/StringsTextFonts/Conceptual/CoreText_Programming/Introduction/Introduction.html)
//有了YYKit之后，这个被打入冷宫？没用上所以没看过
[Core Image Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreImaging/ci_intro/ci_intro.html#//apple_ref/doc/uid/TP30001185-CH1-TPXREF101)
//我倒是想找个能用得上这本的工作，可惜可惜……
[Core Animation Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CoreAnimation_guide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004514-CH1-SW1)
//宁可不工作，也要看这个。但是只看这个还不够……
[]()
//



