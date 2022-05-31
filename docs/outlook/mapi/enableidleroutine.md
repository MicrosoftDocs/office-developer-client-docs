---
title: "EnableIdleRoutine"
description: "EnableIdleRoutine enables or disables a FNIDLE based idle routine. This article describes its syntax, parameters, and remarks."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.EnableIdleRoutine
api_type:
- COM
ms.assetid: 332ea831-bdf9-4dbd-b9c7-a80f8ba11b3b
---

# EnableIdleRoutine

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables or disables a [FNIDLE](fnidle.md) based idle routine. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
VOID EnableIdleRoutine(
  FTG ftg,
  BOOL fEnable
);
```

## Parameters

 _ftg_
  
> [in] Function tag that identifies the idle routine to be enabled or disabled. 
    
 _fEnable_
  
> [in] Contains TRUE if the idle engine should enable the idle routine, or FALSE if it should disable it.
    
## Return value

None.
  
## Remarks

The following functions deal with the MAPI idle engine and with idle routines based on the [FNIDLE](fnidle.md) function prototype: 
  
|**Idle routine function**|**Usage**|
|:-----|:-----|
|[ChangeIdleRoutine](changeidleroutine.md) <br/> |Changes the characteristics of a registered idle routine. |
|[DeregisterIdleRoutine](deregisteridleroutine.md) <br/> |Removes a registered idle routine from the MAPI system. |
|**EnableIdleRoutine** <br/> |Disables or re-enables a registered idle routine without removing it from the MAPI system. |
|[FtgRegisterIdleRoutine](ftgregisteridleroutine.md) <br/> |Adds an idle routine to the MAPI system, with or without enabling it. |
|[MAPIDeInitIdle](mapideinitidle.md) <br/> |Shuts down the MAPI idle engine for the calling application. |
|[MAPIInitIdle](mapiinitidle.md) <br/> |Initializes the MAPI idle engine for the calling application. |
   
 **ChangeIdleRoutine**, **DeregisterIdleRoutine**, and **EnableIdleRoutine** take as an input parameter the function tag returned by **FtgRegisterIdleRoutine**. 
  
When all foreground tasks for the platform become idle, the MAPI idle engine calls the highest priority idle routine that is ready to execute. There is no guarantee of calling order among idle routines of the same priority. 
  

