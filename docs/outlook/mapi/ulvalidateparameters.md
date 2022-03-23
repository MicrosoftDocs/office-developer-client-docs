---
title: "UlValidateParameters"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.UlValidateParameters
api_type:
- COM
ms.assetid: fb9050c9-5797-44f0-8bf5-6264f4e6d7c3
description: "Calls an internal function to check the parameters client applications have passed to service providers and MAPI."
---

# UlValidateParameters

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Calls an internal function to check the parameters client applications have passed to service providers and MAPI. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
HRESULT UlValidateParameters(
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
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_CALL_FAILED 
  
> An error of unexpected or unknown origin prevented the operation from completing.
    
## Remarks

The **UlValidateParameters** macro has been superseded by the [UlValidateParms](ulvalidateparms.md) macro. **UlValidateParameters** does not work correctly on RISC platforms and is now prevented from compiling on them. It still compiles and works correctly on Intel platforms, but **UlValidateParms** is recommended on all platforms. 
  

