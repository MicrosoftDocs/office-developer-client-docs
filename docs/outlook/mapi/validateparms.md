---
title: "ValidateParms"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ValidateParms
api_type:
- COM
ms.assetid: 3ede1a35-4acc-4b8f-a1bd-027f35798a37
description: "Last modified: March 09, 2015"
---

# ValidateParms

  
  
**Applies to**: Outlook 
  
Calls an internal function to check the parameters client applications have passed to service providers. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
HRESULT ValidateParms(
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

Parameters passed between MAPI and service providers are assumed to be correct and undergo only debug validation with the [CheckParms](checkparms.md) macro. Providers should check all parameters passed in by client applications, but clients should assume that MAPI and provider parameters are correct. Use the **HR_FAILED** macro to test return values. 
  
 **ValidateParms** is called differently depending on whether the calling code is C or C++. C++ passes an implicit parameter known as  _this_ to each method call, which becomes explicit in C and is the address of the object. The first parameter,  _eMethod_, is an enumerator made from the interface and method being validated and tells what parameters to expect to find on the stack. The second parameter is different for C and C++. In C++ it is called  _First_, and it is the first parameter to the method being validated. The second parameter for the C language,  _ppThis_, is the address of the first parameter to the method which is always an object pointer. In both cases, the second parameter gives the address of the beginning of the method's parameter list, and based on  _eMethod_, moves down the stack and validates the parameters. 
  
Providers implementing common interfaces such as **IMAPITable** and **IMAPIProp** should always check parameters using the **ValidateParms** function in order to make sure consistency across all providers. Additional parameter validation functions have been defined for some complex parameter types to be used instead as appropriate. See the reference topics for the following functions: 
  
- [FBadColumnSet](fbadcolumnset.md)
    
- [FBadEntryList](fbadentrylist.md)
    
- [FBadProp](fbadprop.md)
    
- [FBadProp](fbadprop.md)
    
- [FBadRestriction](fbadrestriction.md)
    
- [FBadRestriction](fbadrestriction.md)
    
- [FBadRglpszW](fbadrglpszw.md)
    
- [FBadRow](fbadrow.md)
    
- [FBadRowSet](fbadrowset.md)
    
- [FBadSortOrderSet](fbadsortorderset.md)
    
Inherited methods use the same parameter validation as the interface from which they inherit. For example, the parameter checking for **IMessage** and **IMAPIProp** should be the same. 
  
## See also



[UlValidateParms](ulvalidateparms.md)

