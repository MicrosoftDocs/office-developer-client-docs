---
title: "IMAPIFormMgrCalcFormPropSet"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormMgr.CalcFormPropSet
api_type:
- COM
ms.assetid: ab302bfd-5cff-49b4-b0d2-308ae5af478d
description: "Last modified: July 23, 2011"
---

# IMAPIFormMgr::CalcFormPropSet

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns an array of the properties that a group of forms uses.
  
```cpp
HRESULT CalcFormPropSet(
  LPSMAPIFORMINFOARRAY pfrminfoarray,
  ULONG ulFlags,
  LPMAPIFORMPROPARRAY FAR * ppResults
);
```

## Parameters

 _pfrminfoarray_
  
> [in] A pointer to an array of form information objects that identify the forms for which to return properties.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the property array in the  _ppResults_ parameter is returned. The following flags can be set: 
    
FORMPROPSET_INTERSECTION 
  
> The returned array contains the intersection of the form's properties.
    
FORMPROPSET_UNION 
  
> The returned array contains the union of the form's properties.
    
MAPI_UNICODE 
  
> The strings returned in the array are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _ppResults_
  
> [out] A pointer to a pointer to the returned [SMAPIFormPropArray](smapiformproparray.md) structure, which contains the properties that the forms use. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

Form viewers call the **IMAPIFormMgr::CalcFormPropSet** method to obtain an array of the properties that a group of forms uses. **CalcFormPropSet** takes either an intersection or a union of these forms' property sets, depending on the flag set in the  _ulFlags_ parameter, and it returns an **SMAPIFormPropArray** structure that contains the resulting group of properties. 
  
## Notes to implementers

If a form viewer passes the MAPI_UNICODE flag in the  _ulFlags_ parameter, all strings should be returned as Unicode strings. Form library providers that do not support Unicode strings should return MAPI_E_BAD_CHARWIDTH if MAPI_UNICODE is passed. 
  
## See also



[SMAPIFormPropArray](smapiformproparray.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)

