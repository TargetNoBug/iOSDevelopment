## <a name='contents'>Table of Contents</a>
1. [Introduction](#1)
1. [Anatomy of a Run Loop](#2)
1. [When Would You Use a Run Loop?](#3)
1. [Using Run Loop Objects](#4)
1. [Configuring Run Loop Sources](#5)
1. [WCX Summary](#6)


### <a name='1'>Introduction :</a>
Run loops are part of the fundamental infrastructure associated with threads.   
A run loop is an event processing loop that you use to schedule work and coordinate the receipt of incoming events.   
The purpose of a run loop is to keep your thread busy when there is work to do and put your thread to sleep when there is none.

Run loop management is not entirely automatic.   
You must still design your thread’s code to start the run loop at appropriate times and respond to incoming events.   
Both Cocoa and Core Foundation provide run loop objects to help you configure and manage your thread’s run loop.   
Your application does not need to create these objects explicitly; each thread, including the application’s main thread, has an associated run loop object. Only secondary threads need to run their run loop explicitly, however.   
The app frameworks automatically set up and run the run loop on the main thread as part of the application startup process.  

### <a name='2'>Anatomy of a Run Loop :</a>
#### Run Loop Modes
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
``` C

```
