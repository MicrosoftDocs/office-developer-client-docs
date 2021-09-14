---
title: "CheckParms"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CheckParms
api_type:
- COM
ms.assetid: 328f12f0-e4e7-407f-8eb8-0d4bf543962d
description: "Last modified: March 09, 2015"
---

# CheckParms

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Calls an internal function to validate debugging parameters on service provider methods called by MAPI. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
HRESULT CheckParms(
  METHODS eMethod,
  LPVOID First
);
```

## Parameters

 _eMethod_
  
> [in] Specifies, by enumeration, the method to validate. 
    
 _First_
  
> [in] Pointer to the first argument on the stack.
    
## Return value

S_OK 
  
> The call succeeded.
    
## Remarks

In contrast to the [ValidateParms](validateparms.md) and [UlValidateParms](ulvalidateparms.md) macros, the **CheckParms** macro does not perform a full parameter validation. Parameters passed between MAPI and service providers are assumed to be correct, so **CheckParms** performs a debug validation only. 
  

