---
title: "MAPI Idle Engine"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 755d096a-2a61-44d2-a765-5d464a857756
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Idle Engine

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
MAPI provides several functions that are collectively known as the idle engine. These functions allow clients, address book providers, and message store providers to perform various tasks during slow times in the session or in response to a slow time. For example, clients and service providers can defer slow operations or close files that have remained unused for a lengthy period. Transport providers typically do not use the idle engine because the **IXPLogon::Idle** method takes its place. For more information, see [IXPLogon::Idle](ixplogon-idle.md).
  
To use the idle engine, clients and service providers create a callback function that contains the tasks that should occur when the MAPI subsystem is idle. When MAPI detects idle time, it invokes this callback function. The callback function follows the **FNIDLE** prototype, defined as follows: 
  
 `BOOL (STDAPICALLTYPE FNIDLE) (LPVOID lpvContext)`
  
For more information, see [FNIDLE](fnidle.md).
  
The functions that make up the idle engine are:
  
[ChangeIdleRoutine](changeidleroutine.md)
  
[DeregisterIdleRoutine](deregisteridleroutine.md)
  
[EnableIdleRoutine](enableidleroutine.md)
  
[FtgRegisterIdleRoutine](ftgregisteridleroutine.md)
  
[MAPIDeInitIdle](mapideinitidle.md)
  
[MAPIInitIdle](mapiinitidle.md)
  
To register a callback function, clients and service providers call the **FtgRegisterIdleRoutine** function. The input parameters include an optional priority, a block of memory that is passed to your callback function as input, an amount of time to be used in any way appropriate, and a set of option flags. 
  
Clients and service providers can specify a priority in the  _priIdle_ parameter that controls how the idle function runs or specify zero if priority is not an issue. Because negative numbers represent higher priorities than positive numbers or zero, compression and search operations should be assigned negative numbers. Tasks that occur once should be assigned positive numbers. 
  
To deregister an active callback function, clients and service providers call the **DeregisterIdleRoutine** function. Because **DeregisterIdleRoutine** operates asynchronously, it is possible for the callback function to be invoked at any time during the deregister call and possibly even after **DeregisterIdleRoutine** has returned. 
  
To modify some or all of the characteristics of a callback function, clients and service providers call the **ChangeIdleRoutine** function. **ChangeIdleRoutine** makes changes according to how the flags parameter  _ircIdle_ is set; **ChangeIdleRoutine** can change the function itself, its priority, time setting, and input parameter. 
  
MAPI defines idle the same as the operating system, when the operating system has a definition. On Win32, MAPI creates a thread with idle-class priority to schedule idle tasks. This thread keeps track of the time and posts a message to the thread that is to execute the idle task when the time for its execution arrives. Win32 schedules threads, not processes. If tasks that have a priority higher than the idle priority are occurring on the workstation, the idle task should not get scheduled for execution until the tasks have completed. 
  
All idle tasks run on the thread that called **MAPIInitIdle**. MAPI has a separate thread for scheduling, but when an idle task becomes eligible, it posts a message back over to the initialization thread and the idle task is executed there. The implications for different types of clients are as follows.
  
|**Threading model**|**Implication**|
|:-----|:-----|
|Single-threaded  <br/> |No problem. Idle functions execute on your client's main thread and are serialized through the message loop.  <br/> |
|Free-threaded  <br/> |Idle functions must be thread-safe, but your client already has the necessary infrastructure. Your client might not need the MAPI idle engine at all.  <br/> |
|Apartment-threaded  <br/> |Idle function has to execute on the same thread that registered it if it wants to use MAPI, OLE, or any other COM interfaces. The most straightforward way is to register an idle function with MAPI that posts a message to the right thread and dispatch the "real" idle function directly from that thread's message loop.  <br/> |
   

