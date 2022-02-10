---
title: "FtgRegisterIdleRoutine"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FtgRegisterIdleRoutine
api_type:
- COM
ms.assetid: 8d9557ba-7919-42c6-9e2f-f10214437d53
description: "Last modified: March 09, 2015"
---

# FtgRegisterIdleRoutine

**Applies to**: Outlook 2013 | Outlook 2016 
  
Adds a [FNIDLE](fnidle.md) function-based idle routine to the MAPI system. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
FTG FtgRegisterIdleRoutine(
  PFNIDLE pfnIdle,
  LPVOID pvIdleParam,
  short priIdle,
  ULONG csecIdle,
  USHORT iroIdle
);
```

## Parameters

_pfnIdle_
  
> [in] A pointer to the idle routine. 
    
_pvIdleParam_
  
> [in] A pointer to a block of memory that the idle engine should pass as a parameter to the idle routine when it calls it. 
    
_priIdle_
  
> [in] The initial priority for the idle routine. Possible priorities for implementation-defined routines are greater than or less than zero, but not zero. The zero priority is reserved for a user event such as a mouse click or a WM_PAINT message. Priorities greater than zero represent background tasks that have a higher priority than user events and are dispatched as part of the standard Windows message pump loop. Priorities less than zero represent idle tasks that only run during message pump idle time. Examples of priorities are as follows: 1 for foreground submission, 2 for power-edit character insertion, and 3 for downloading new messages.
    
_csecIdle_
  
> [in] The initial time value, in hundredths of a second, to be used in specifying idle routine parameters. The meaning of the initial time value varies, depending on what is passed in the _iroIdle_ parameter. The meaning can be one of the following: 
    
  - The minimum period of user inaction that must elapse before the MAPI idle engine calls the idle routine for the first time, if the FIROWAIT flag is set in  _iroIdle_. After this time passes, the idle engine can call the idle routine as often as necessary. 
    
  - The minimum interval between calls to the idle routine, if the FIROINTERVAL flag is set in  _iroIdle_. 
    
_iroIdle_
  
> [in] The bitmask of flags used to set initial options for the idle routine. The following flags can be set:
    
  FIRONOADJUSTMENT
    
  > Use this flag to specify that the idle routine timer should not be adjusted for sleep or resume. The default behavior without this flag is that sleep time is excluded when calculating the elapsed time. If FIRONOADJUSTMENT is passed then the sleep time is included when calculating elapsed time.
      
  FIRODISABLED
    
  > The idle routine should be disabled when registered. The default action is to enable the idle routine when **FtgRegisterIdleRoutine** registers it. 
      
  FIROINTERVAL 
    
  > The time specified by the  _csecIdle_ parameter is the minimum interval between successive calls to the idle routine. 
      
  FIROONCEONLY 
    
  > Obsolete. Do not use. 
      
  FIROPERBLOCK 
    
  > Obsolete. Do not use. 
      
  FIROWAIT 
    
  > The time specified by the  _csecIdle_ parameter is the minimum period of user inaction that must elapse before the MAPI idle engine calls the idle routine for the first time. After this time passes, the idle engine can call the idle routine as often as necessary. 
    
## Return value

The **FtgRegisterIdleRoutine** function returns a function tag identifying the idle routine that was added to the MAPI system. If **FtgRegisterIdleRoutine** cannot register the idle routine for the client application or service provider, for example because of memory problems, it returns NULL. 
  
## Remarks

The following functions deal with the MAPI idle engine and with idle routines based on the [FNIDLE](fnidle.md) function prototype. 
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|[ChangeIdleRoutine](changeidleroutine.md) <br/> |Changes the characteristics of a registered idle routine. |
|[DeregisterIdleRoutine](deregisteridleroutine.md) <br/> |Removes a registered idle routine from the MAPI system. |
|[EnableIdleRoutine](enableidleroutine.md) <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system. |
|**FtgRegisterIdleRoutine** <br/> |Adds an idle routine to the MAPI system, with or without enabling it. |
|[MAPIDeInitIdle](mapideinitidle.md) <br/> |Shuts down the MAPI idle engine for the calling application. |
|[MAPIInitIdle](mapiinitidle.md) <br/> |Initializes the MAPI idle engine for the calling application. |
   
**ChangeIdleRoutine**, **DeregisterIdleRoutine**, and **EnableIdleRoutine** take as an input parameter the function tag returned by **FtgRegisterIdleRoutine**. 
  
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority. 
  
The following is an example of using the FIRONOADJUSTMENT flag in the _iroIdle_ parameter. 
  
1. Register an idle routine with a 5 minute delay.
    
2. Hibernate/Sleep the computer after 1 minute (4 minutes left on the timer).
    
3. Resume the computer 10 minutes later.
    
The default behavior, without FIRONOADJUSTMENT, is that you still have to wait 4 more minutes for your routine to run. That is, your timer was adjusted to allow for how long the computer was asleep. However, if you pass FIRONOADJUSTMENT your idle routine will run immediately because more than 5 minutes of real time have elapsed.
  

