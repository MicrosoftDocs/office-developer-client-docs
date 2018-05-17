---
title: "MAPIDeInitIdle"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MAPIDeInitIdle
api_type:
- COM
ms.assetid: f7b04486-bc48-4ba4-9f35-f021e06124bf
description: "Last modified: March 09, 2015"
---

# MAPIDeInitIdle

  
  
**Applies to**: Outlook 
  
Shuts down the MAPI idle engine for the calling application. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
void MAPIDeInitIdle( void );
```

## Parameters

None. 
  
## Return value

None.
  
## Remarks

A client application or service provider should call **MAPIDeInitIdle** when it no longer needs the idle engine, for example, when it is about to stop processing. 
  
Every call to [MAPIInitIdle](mapiinitidle.md) must be matched by a subsequent call to **MAPIDeInitIdle**, or the idle engine is left running for the calling application. 
  
The following functions deal with the MAPI idle engine and with idle routines based on the [FNIDLE](fnidle.md) function prototype: 
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|[ChangeIdleRoutine](changeidleroutine.md) <br/> |Changes the characteristics of a registered idle routine.  <br/> |
|[DeregisterIdleRoutine](deregisteridleroutine.md) <br/> |Removes a registered idle routine from the MAPI system.  <br/> |
|[EnableIdleRoutine](enableidleroutine.md) <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system.  <br/> |
|[FtgRegisterIdleRoutine](ftgregisteridleroutine.md) <br/> |Adds an idle routine to the MAPI system, with or without enabling it.  <br/> |
|**MAPIDeInitIdle** <br/> |Shuts down the MAPI idle engine for the calling application.  <br/> |
|[MAPIInitIdle](mapiinitidle.md) <br/> |Initializes the MAPI idle engine for the calling application.  <br/> |
   
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority. 
  

