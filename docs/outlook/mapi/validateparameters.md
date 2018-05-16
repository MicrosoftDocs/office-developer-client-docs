---
title: "ValidateParameters"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ValidateParameters
api_type:
- COM
ms.assetid: 80aadd11-5409-4636-8fad-fa2206336671
description: "Last modified: March 09, 2015"
---

# ValidateParameters

  
  
**Applies to**: Outlook 
  
Calls an internal function to check the parameters client applications have passed to service providers. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```
HRESULT ValidateParameters(
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
  
> All of the parameters are valid. 
    
MAPI_E_CALL_FAILED 
  
> One or more of the parameters are not valid.
    
## Remarks

The **ValidateParameters** macro has been superseded by the [ValidateParms](validateparms.md) macro. **ValidateParameters** does not work correctly on RISC platforms and is now prevented from compiling on them. It still compiles and works correctly on Intel platforms, but **ValidateParms** is recommended on all platforms. 
  

