---
title: "MAPIInitIdle"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MAPIInitIdle
api_type:
- COM
ms.assetid: b6de7c6a-f2e7-4248-adea-d354924a8bbf
description: "Last modified: March 09, 2015"
---

# MAPIInitIdle

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Initializes the MAPI idle engine for the calling application. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
LONG MAPIInitIdle(
  LPVOID lpvReserved
);
```

## Parameters

 _lpvReserved_
  
> [in] Reserved; must be zero.
    
## Return value

The **MAPIInitIdle** function returns zero if initialization is successful, and 1 otherwise. If **MAPIInitIdle** is called multiple times, all additional calls succeed but are ignored except to increment the reference count. 
  
## Remarks

A client application or service provider must call **MAPIInitIdle** before calling any other idle engine function. 
  
Every call to **MAPIInitIdle** must be matched by a subsequent call to [MAPIDeInitIdle](mapideinitidle.md), or the idle engine is left running for the calling application. 
  
The following functions deal with the MAPI idle engine and with idle routines based on the [FNIDLE](fnidle.md) function prototype: 
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|[ChangeIdleRoutine](changeidleroutine.md) <br/> |Changes the characteristics of a registered idle routine.  <br/> |
|[DeregisterIdleRoutine](deregisteridleroutine.md) <br/> |Removes a registered idle routine from the MAPI system.  <br/> |
|[EnableIdleRoutine](enableidleroutine.md) <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system.  <br/> |
|[FtgRegisterIdleRoutine](ftgregisteridleroutine.md) <br/> |Adds an idle routine to the MAPI system, with or without enabling it.  <br/> |
|[MAPIDeInitIdle](mapideinitidle.md) <br/> |Shuts down the MAPI idle engine for the calling application.  <br/> |
|**MAPIInitIdle** <br/> |Initializes the MAPI idle engine for the calling application.  <br/> |
   
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority. 
  

