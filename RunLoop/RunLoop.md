## <a name='contents'>Table of Contents</a>

1. [Preparation](#Preparation)
1. [Defination](#Defination)
1. [Reference](#Reference)
1. [Function](#Function)
1. [Relationships](#Relationships)
1. [Usage](#Usage)
1. [Reference](#Reference)
1. [Questions](#Questions)
### <a name='Preparation'>Preparation:</a> . 
#### CFRunLoop source code
CFRunLoop是属于Core Foundation的，从[](https://opensource.apple.com/source/CF/)能看到部分CF的source code，经过对比，我选择这个2015的[CFRunLoop SRC](https://opensource.apple.com/source/CF/CF-1153.18/CFRunLoop.c.auto.html)  
**有了source code还不够，还需要有看src的方法……**  
Data+Alogrithm
#### C语言: 
[pointer](https://github.com/saint-shaka/CHowToProgram8thNotes/blob/master/07.C%20Pointers.md)  
[structure](https://github.com/saint-shaka/CHowToProgram8thNotes/blob/master/10.C%20Structures,%20Unions,%20Bit%20Manipulation%20and%20Enumerations.md)   
pthread
#### 操作系统: 线程相关的

 
### <a name='Defination'>Defination:</a> . 
 **A run loop is an event processing loop that you use to schedule work and coordinate the receipt of incoming events. The purpose of a run loop is to keep your thread busy when there is work to do and put your thread to sleep when there is none.**  

**You must still design your thread’s code to start the run loop at appropriate times and respond to incoming events. Both Cocoa and Core Foundation provide run loop objects to help you configure and manage your thread’s run loop. Your application does not need to create these objects explicitly; each thread, including the application’s main thread, has an associated run loop object. Only secondary threads need to run their run loop explicitly, however. The app frameworks automatically set up and run the run loop on the main thread as part of the application startup process.**

### <a name='Reference'>Reference:</a>  

### <a name='Function'>Function:</a>  

### <a name='Relationships'>Relationships:</a>

### <a name='Usage'>Usage:</a>

### <a name='Reference'>Reference:</a> 

[Threading PG-RunLoop](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/RunLoopManagement/RunLoopManagement.html#//apple_ref/doc/uid/10000057i-CH16-SW1) . 

[YY](https://blog.ibireme.com/2015/05/18/runloop/) . 

[CuiJT](https://www.cnblogs.com/kenshincui/p/6823841.html) . 
 
### <a name='Questions'>Questions:</a>  


### <a name=''>:</a>  


