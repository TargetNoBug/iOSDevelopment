## <a name='contents'>Table of Contents</a>
1. [Introduction](#1)
1. [Anatomy of a Run Loop](#2)
1. [When Would You Use a Run Loop?](#3)
1. [Using Run Loop Objects](#4)
1. [Configuring Run Loop Sources](#5)
1. [WCX Summary](#6)


### <a name='1'>Introduction :</a>
Run loops are part of the fundamental infrastructure associated with threads.   
**A run loop is an event processing loop that you use to schedule work and coordinate the receipt of incoming events.**   
The purpose of a run loop is to keep your thread busy when there is work to do and put your thread to sleep when there is none.

Run loop management is not entirely automatic.   
You must still design your thread’s code to start the run loop at appropriate times and respond to incoming events.   
Both Cocoa and Core Foundation provide run loop objects to help you configure and manage your thread’s run loop.   
Your application does not need to create these objects explicitly; each thread, including the application’s main thread, has an associated run loop object. Only secondary threads need to run their run loop explicitly, however.   
The app frameworks automatically set up and run the run loop on the main thread as part of the application startup process.  

### <a name='2'>Anatomy of a Run Loop :</a>
A run loop is very much like its name sounds. It is a loop your thread enters and uses to run event handlers in response to incoming events. Your code provides the control statements used to implement the actual loop portion of the run loop—in other words, your code provides the while or for loop that drives the run loop. Within your loop, you use a run loop object to "run” the event-processing code that receives events and calls the installed handlers.

A run loop receives events from two different types of sources. Input sources deliver asynchronous events, usually messages from another thread or from a different application. Timer sources deliver synchronous events, occurring at a scheduled time or repeating interval. Both types of source use an application-specific handler routine to process the event when it arrives.

Figure 3-1 shows the conceptual structure of a run loop and a variety of sources. The input sources deliver asynchronous events to the corresponding handlers and cause the runUntilDate: method (called on the thread’s associated NSRunLoop object) to exit. Timer sources deliver events to their handler routines but do not cause the run loop to exit.
![Figure 3-1  Structure of a run loop and its sources](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/Art/runloop.jpg)

In addition to handling sources of input, run loops also generate notifications about the run loop’s behavior. Registered run-loop observers can receive these notifications and use them to do additional processing on the thread. You use Core Foundation to install run-loop observers on your threads.

The following sections provide more information about the components of a run loop and the modes in which they operate. They also describe the notifications that are generated at different times during the handling of events.


#### Run Loop Modes
A run loop mode is a collection of input sources and timers to be monitored and a collection of run loop observers to be notified. Each time you run your run loop, you specify (either explicitly or implicitly) a particular “mode” in which to run. During that pass of the run loop, only sources associated with that mode are monitored and allowed to deliver their events. (Similarly, only observers associated with that mode are notified of the run loop’s progress.) Sources associated with other modes hold on to any new events until subsequent passes through the loop in the appropriate mode.

#### Input Sources
* Port-Based Sources
* Custom Input Sources
* Cocoa Perform Selector Sources
#### Timer Sources
#### Run Loop Observers
#### The Run Loop Sequence of Events

``` C

```
### <a name='3'>When Would You Use a Run Loop :</a>
The **only** time you need to run a run loop explicitly is when you create secondary threads for your application.   

Run loops are intended for situations where you want more interactivity with the thread. For example, you need to start a run loop if you plan to do any of the following:  
* Use ports or custom input sources to communicate with other threads.  
* Use timers on the thread.  
* Use any of the performSelector… methods in a Cocoa application.  
* Keep the thread around to perform periodic tasks.  

``` C

```
### <a name='4'>Using Run Loop Objects :</a>
#### Getting a Run Loop Object
#### Configuring the Run Loop
#### Starting the Run Loop
#### Exiting the Run Loop
#### Thread Safety and Run Loop Objects
``` C

```
### <a name='5'>Configuring Run Loop Sources :</a>
#### Defining a Custom Input Source
* Defining the Input Source
* Installing the Input Source on the Run Loop
* Coordinating with Clients of the Input Source
* Signaling the Input Source
#### Configuring Timer Sources
#### Configuring a Port-Based Input Source
* Configuring an NSMachPort Object
* Configuring an NSMessagePort Object
* Configuring a Port-Based Input Source in Core Foundation
``` C

```
### <a name='6'>WCX Summary :</a>
基本线索：  
RunLoop 是什么？  
A run loop is an event processing loop that you use to schedule work and coordinate the receipt of incoming events.

RunLoop 要处理的events有几种类型？分别是什么？  
A run loop receives events from two different types of sources.  
Input sources deliver asynchronous events, usually messages from another thread or from a different application.  
Timer sources deliver synchronous events, occurring at a scheduled time or repeating interval.  

能不能手画出这张图？
![Figure 3-1  Structure of a run loop and its sources](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/Art/runloop.jpg)

RunLoop除了handle input sources，还能干什么？  
generate notifications about the run loop’s behavior for RunLoop Observers(CFRunLoopObserver).  

为什么要设计CFRunLoopObserver这个类？  
receive notifications and use them to do additional processing on the thread.   
//类似delegate？避免把additional processing on the thread写在CFRunLoopObserver的src里？  

一句话总结：  
RunLoop是干什么用的？  
**为了控制thread的busy/sleep状态，设计了RunLoop, 用来处理input sources 或 timer sources，并把相关的notification发送给registered RunLoop observers, 让这些observers能进行进一步处理.**

RunLoopMode的作用是什么？  
用来指定RunLoop是处理input sources还是timer sources的。指定了要处理的source，就会把相关的notification发送给registered RunLoop observers.
//也就我这种厚颜无耻之人才会想到这种场景（求更佳场景）：
某男(NSRunLoop)有2个女友(sources)，一个是年轻漂亮的小女友(input source)，但是没钱；另一个是老且丑的富婆(timer source)，但是有钱。
不需要钱的时候，进入NSDefaultRunLoopMode，只和小女友打情骂俏，冷落富婆；需要钱的时候，进入NSRunLoopCommonModes，专心伺候富婆，冷落小女友。

进阶问题:  
设计RunLoop的目的是什么？
The purpose of a run loop is to keep your thread busy when there is work to do and put your thread to sleep when there is none.
