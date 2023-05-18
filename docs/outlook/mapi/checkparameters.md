---
title: "CheckParameters"
description: "CheckParameters calls an internal function to validate debugging parameters on service provider methods called by MAPI."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CheckParameters
api_type:
- COM
ms.assetid: ba33866a-c9c4-454a-9549-72455c61ee97
---

# CheckParameters

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Calls an internal function to validate debugging parameters on service provider methods called by MAPI. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
HRESULT CheckParameters(
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

The **CheckParameters** macro has been superseded by the [CheckParms](checkparms.md) macro. **CheckParms** is recommended on all platforms. 
  

