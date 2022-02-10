---
title: "DeregisterIdleRoutine"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DeregisterIdleRoutine
api_type:
- COM
ms.assetid: a8ada6fe-9963-4c25-b4b4-db77f9517368
description: "Last modified: March 09, 2015"
---

# DeregisterIdleRoutine

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Removes a [FNIDLE](fnidle.md) based idle routine from the MAPI system. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
VOID DeregisterIdleRoutine(
  FTG ftg
);
```

## Parameters

 _ftg_
  
> [in] Function tag that identifies the idle routine to be removed.
    
## Return value

None.
  
## Remarks

Any task in a client application or service provider can deregister any idle routine for which it has a valid  _ftg_ parameter. In particular, an idle routine can deregister itself. 
  
The following functions deal with the MAPI idle engine and with idle routines based on the [FNIDLE](fnidle.md) function prototype: 
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|[ChangeIdleRoutine](changeidleroutine.md) <br/> |Changes the characteristics of a registered idle routine. |
|**DeregisterIdleRoutine** <br/> |Removes a registered idle routine from the MAPI system. |
|[EnableIdleRoutine](enableidleroutine.md) <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system. |
|[FtgRegisterIdleRoutine](ftgregisteridleroutine.md) <br/> |Adds an idle routine to the MAPI system, with or without enabling it. |
|[MAPIDeInitIdle](mapideinitidle.md) <br/> |Shuts down the MAPI idle engine for the calling application. |
|[MAPIInitIdle](mapiinitidle.md) <br/> |Initializes the MAPI idle engine for the calling application. |
   
 **ChangeIdleRoutine**, **DeregisterIdleRoutine**, and **EnableIdleRoutine** take as an input parameter the function tag returned by **FtgRegisterIdleRoutine**. 
  
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority. 
  
After the idle routine is deregistered, the idle engine does not call it again. Any implementation that calls **DeregisterIdleRoutine** must deallocate any memory blocks to which it passed pointers for the idle engine to use in its original call to the **FtgRegisterIdleRoutine** function. 
  

