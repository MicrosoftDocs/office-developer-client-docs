---
title: "FNIDLE"
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FNIDLE
api_type:
- COM
ms.assetid: f6b31bb4-69dd-43de-b62b-abfa99557641
description: "Defines an idle routine that the MAPI idle engine calls periodically according to priority."
---

# FNIDLE

**Applies to**: Outlook 2013 | Outlook 2016
  
Defines an idle routine that the MAPI idle engine calls periodically according to priority.
  
|**Property**|**Value**|
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Defined function implemented by:  <br/> |Client applications and service providers  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
|Corresponding pointer type:  <br/> |PFNIDLE  <br/> |

```cpp
BOOL (STDAPICALLTYPE FNIDLE)(
  LPVOID lpvContext
);
```

## Parameters

 _lpvContext_
  
> [in] Pointer to a block of memory that MAPI passes to the idle routine each time it calls it. This pointer is passed to the MAPI idle engine in the _pvIdleParam_ parameter by [FtgRegisterIdleRoutine](ftgregisteridleroutine.md). The data in the memory block can provide context for the call to the idle routine, such as which object to operate on, or the current state of a lengthy operation.

## Return value

FALSE
  
> An idle routine with the **FNIDLE** prototype should always return FALSE.

## Remarks

The specific functionality of the idle routine is determined by the implementing client application or service provider.
  
The client or provider must limit the execution time of each state of an idle routine. Every state should perform a minimum amount of processing, update the current state in the context data pointed to by _lpvContext_, and return to the MAPI idle engine.
  
The client or provider must call the MAPI function [MAPIInitIdle](mapiinitidle.md) before it can register its own idle routine with a call to the [FtgRegisterIdleRoutine](ftgregisteridleroutine.md) function.
  
The following functions deal with the MAPI idle engine and with idle routines based on the FNIDLE function prototype:
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|[ChangeIdleRoutine](changeidleroutine.md) <br/> |Changes the characteristics of a registered idle routine. |
|[DeregisterIdleRoutine](deregisteridleroutine.md) <br/> |Removes a registered idle routine from the MAPI system. |
|[EnableIdleRoutine](enableidleroutine.md) <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system. |
|[FtgRegisterIdleRoutine](ftgregisteridleroutine.md) <br/> |Adds an idle routine to the MAPI system, with or without enabling it. |
|[MAPIDeInitIdle](mapideinitidle.md) <br/> |Shuts down the MAPI idle engine for the calling application. |
|[MAPIInitIdle](mapiinitidle.md) <br/> |Initializes the MAPI idle engine for the calling application. |

**ChangeIdleRoutine**, **DeregisterIdleRoutine**, and **EnableIdleRoutine** take as an input parameter the function tag returned by **FtgRegisterIdleRoutine**.
  
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority.
  