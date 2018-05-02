---
title: "UlValidateParms"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.UlValidateParms
api_type:
- COM
ms.assetid: 02c66b46-1f01-43fb-832c-bac27aaae19f
description: "Last modified: March 09, 2015"
---

# UlValidateParms

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Calls an internal function to check the parameters client applications have passed to service providers and MAPI. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```
HRESULT UlValidateParms(
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
  
> An error prevented the operation from completing.
    
## Remarks

Parameters passed between MAPI and service providers are assumed to be correct and undergo only debug validation with the [CheckParms](checkparms.md) macro. Providers should check all parameters passed in by client applications, but clients should assume that MAPI and provider parameters are correct. Use the **HR_FAILED** macro to test return values. 
  
The **UlValidateParms** macro is called differently depending on whether the calling code is C or C++. This macro is used to validate parameters for the few **IUnknown** and MAPI methods that return ULONG instead of HRESULT values; the [ValidateParms](validateparms.md) macro works for all others. 
  

