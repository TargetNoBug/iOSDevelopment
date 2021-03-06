本人又笨又懒，Apple Dev文档又坑，所以没人要了……

## <a name='contents'>Table of Contents</a>

1. [Preparation](#Preparation)
1. [Glossary](#Glossary)
1. [References](#References)
1. [Source Code](#SRC)
1. [Relationships](#Relationships)
1. [Usage](#Usage)
1. [Questions](#Questions)
### <a name='Preparation'>Preparation:</a> . 
看文档之前需要的基础：
Data+Alogrithm
#### C语言: 
[pointer](https://github.com/saint-shaka/CHowToProgram8thNotes/blob/master/07.C%20Pointers.md)  
[structure(含Union)](https://github.com/saint-shaka/CHowToProgram8thNotes/blob/master/10.C%20Structures,%20Unions,%20Bit%20Manipulation%20and%20Enumerations.md)   
pthread
#### 操作系统: 线程相关的  
看看这个也有好处[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/EventArchitecture/EventArchitecture.html#//apple_ref/doc/uid/10000060i-CH3-SW11)  

#### CFRunLoop source code
CFRunLoop是属于Core Foundation的，从[](https://opensource.apple.com/source/CF/)能看到部分CF的source code，经过对比，我选择这个2015的[CFRunLoop SRC](https://opensource.apple.com/source/CF/CF-1153.18/CFRunLoop.c.auto.html)  
**有了source code还不够，还需要有看src的方法……**
比如，  
[1](https://github.com/aredridel/how-to-read-code/blob/master/how-to-read-code.md)  
[2](http://himmele.blogspot.com/2012/01/how-do-you-read-source-code.html)  

### <a name='Glossary'>Glossary:</a> . 
* RunLoop:
* RunLoop Sources:
* RunLoopMode:
* RunLoopObserver:
* Input Sources:
* Timer Sources:
* 
* 
* 
* 
* 
* 
* 
### <a name='References'>References:</a>  
[Threading Programming Guide-RunLoops](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/RunLoopManagement/RunLoopManagement.html#//apple_ref/doc/uid/10000057i-CH16-SW1)  
[NSRunLoop](https://developer.apple.com/documentation/foundation/nsrunloop?language=occ) .  
[CFRunLoop](https://developer.apple.com/documentation/corefoundation/cfrunloop-rht) .  
[CFRunLoopMode(没内容)](https://developer.apple.com/documentation/corefoundation/cfrunloopmode?language=objc) .   
[CFRunLoopObserver(就一句话)](https://developer.apple.com/documentation/corefoundation/cfrunloopobserver) .   
[CFRunLoopTimer](https://developer.apple.com/documentation/corefoundation/cfrunlooptimer-rhk) .   
[]() .   
[]() .   
[]() .   
[YY](https://blog.ibireme.com/2015/05/18/runloop/) .  
[CuiJT](https://www.cnblogs.com/kenshincui/p/6823841.html) .  
### <a name='SRC'>Source Code:</a>  
**A CFRunLoop object monitors sources of input to a task and dispatches control when they become ready for processing.**
```C
struct __CFRunLoop {
    CFRuntimeBase _base;
    pthread_mutex_t _lock;            /* locked for accessing mode list */
    __CFPort _wakeUpPort;            // used for CFRunLoopWakeUp
    Boolean _unused;
    volatile _per_run_data *_perRunData;              // reset for runs of the run loop
    pthread_t _pthread;
    uint32_t _winthread;
    CFMutableSetRef _commonModes;/*需要学习*/
    CFMutableSetRef _commonModeItems;
    CFRunLoopModeRef _currentMode;
    CFMutableSetRef _modes;
    struct _block_item *_blocks_head;
    struct _block_item *_blocks_tail;
    CFAbsoluteTime _runTime;
    CFAbsoluteTime _sleepTime;
    CFTypeRef _counterpart;
};
```
**A run loop mode is a collection of input sources and timers to be monitored and a collection of run loop observers to be notified.**
```C
struct __CFRunLoopMode {
    CFRuntimeBase _base;
    pthread_mutex_t _lock;    /* must have the run loop locked before locking this */
    CFStringRef _name;
    Boolean _stopped;
    char _padding[3];
    CFMutableSetRef _sources0;/*需要学习*/
    CFMutableSetRef _sources1;/*需要学习*/
    CFMutableArrayRef _observers;/*需要学习*/
    CFMutableArrayRef _timers;/*需要学习*/
    CFMutableDictionaryRef _portToV1SourceMap;
    __CFPortSet _portSet;
    CFIndex _observerMask;
#if USE_DISPATCH_SOURCE_FOR_TIMERS
    dispatch_source_t _timerSource;
    dispatch_queue_t _queue;
    Boolean _timerFired; // set to true by the source when a timer has fired
    Boolean _dispatchTimerArmed;
#endif
#if USE_MK_TIMER_TOO
    mach_port_t _timerPort;
    Boolean _mkTimerArmed;
#endif
#if DEPLOYMENT_TARGET_WINDOWS
    DWORD _msgQMask;
    void (*_msgPump)(void);
#endif
    uint64_t _timerSoftDeadline; /* TSR */
    uint64_t _timerHardDeadline; /* TSR */
};
```
**Both types of source use an application-specific handler routine to process the event when it arrives.**
```C
struct __CFRunLoopSource {
    CFRuntimeBase _base;
    uint32_t _bits;
    pthread_mutex_t _lock;
    CFIndex _order;			/* immutable */
    CFMutableBagRef _runLoops;
    union {
       	CFRunLoopSourceContext version0;	/* immutable, except invalidation */
        CFRunLoopSourceContext1 version1;	/* immutable, except invalidation */
    } _context;
};
```
**In addition to handling sources of input, run loops also generate notifications about the run loop’s behavior. Registered run-loop observers can receive these notifications and use them to do additional processing on the thread.**
```C
struct __CFRunLoopObserver {
    CFRuntimeBase _base;
    pthread_mutex_t _lock;
    CFRunLoopRef _runLoop;
    CFIndex _rlCount;
    CFOptionFlags _activities;		/* immutable */
    CFIndex _order;			/* immutable */
    CFRunLoopObserverCallBack _callout;	/* immutable */
    CFRunLoopObserverContext _context;	/* immutable, except invalidation */
};
```
**A CFRunLoopTimer object represents a specialized run loop source that fires at a preset time in the future.**
```C
struct __CFRunLoopTimer {
    CFRuntimeBase _base;
    uint16_t _bits;
    pthread_mutex_t _lock;
    CFRunLoopRef _runLoop;
    CFMutableSetRef _rlModes;
    CFAbsoluteTime _nextFireDate;
    CFTimeInterval _interval;		/* immutable */
    CFTimeInterval _tolerance;          /* mutable */
    uint64_t _fireTSR;			/* TSR units */
    CFIndex _order;			/* immutable */
    CFRunLoopTimerCallBack _callout;	/* immutable */
    CFRunLoopTimerContext _context;	/* immutable, except invalidation */
};
```
### <a name='Relationships'>Relationships:</a>

### <a name='Usage'>Usage:</a>


### <a name='Questions'>Questions:</a>  


### <a name=''>:</a>  


