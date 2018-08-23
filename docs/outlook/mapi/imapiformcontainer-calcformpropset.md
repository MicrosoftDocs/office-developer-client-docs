---
title: "IMAPIFormContainerCalcFormPropSet"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormContainer.CalcFormPropSet
api_type:
- COM
ms.assetid: 594e3aac-a00f-422e-8e7a-949e4c9a3f8d
description: "Last modified: July 23, 2011"
---

# IMAPIFormContainer::CalcFormPropSet

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns an array of the properties used by all forms installed in a form container.
  
```cpp
HRESULT CalcFormPropSet(
  ULONG ulFlags,
  LPMAPIFORMPROPARRAY FAR * ppResults
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how the property array in the  _ppResults_ parameter is returned. The following flags can be set: 
    
FORMPROPSET_INTERSECTION 
  
> The returned array contains the intersection of the forms' properties.
    
FORMPROPSET_UNION 
  
> The returned array contains the union of the forms' properties.
    
MAPI_UNICODE 
  
> The strings returned in the array are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _ppResults_
  
> [out] A pointer to a pointer to the returned [SMAPIFormPropArray](smapiformproparray.md) structure. This structure contains all properties used by the installed forms. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

Client applications call the **IMAPIFormContainer::CalcFormPropSet** method to obtain an array of properties used by all forms installed in a form container. **IMAPIFormContainer::CalcFormPropSet** works like the [IMAPIFormMgr::CalcFormPropSet](imapiformmgr-calcformpropset.md) method, except that it operates on every form registered in a particular container. 
  
## Notes to implementers

Form library providers that do not support Unicode strings should return MAPI_E_BAD_CHARWIDTH if MAPI_UNICODE is passed.
  
## Notes to callers

 **IMAPIFormContainer::CalcFormPropSet** takes either an intersection or a union of the forms' property sets, depending on the flag set in the  _ulFlags_ parameter, and it returns an **SMAPIFormPropArray** structure that contains the resulting group of properties. 
  
If a client passes the MAPI_UNICODE flag in  _ulFlags_, all returned strings are Unicode.
  
## See also



[IMAPIFormMgr::CalcFormPropSet](imapiformmgr-calcformpropset.md)
  
[SMAPIFormPropArray](smapiformproparray.md)
  
[IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md)

