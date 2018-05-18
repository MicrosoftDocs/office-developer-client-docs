---
title: "IMAPIFormInfoCalcVerbSet"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormInfo.CalcVerbSet
api_type:
- COM
ms.assetid: 0170dc9d-dc72-48e2-a522-374f199b18ea
description: "Last modified: March 09, 2015"
---

# IMAPIFormInfo::CalcVerbSet

  
  
**Applies to**: Outlook 
  
Returns a pointer to the complete set of verbs that a form uses.
  
```cpp
HRESULT CalcVerbSet(
  ULONG ulFlags,
  LPMAPIVERBARRAY FAR * ppMAPIVerbArray
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The returned strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _ppMAPIVerbArray_
  
> [out] A pointer to a pointer to the returned [SMAPIVerbArray](smapiverbarray.md) structure that contains the form's verbs. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

Client applications call the **IMAPIFormInfo::CalcVerbSet** method to obtain a pointer to the set of verbs used by a form. In the **SMAPIVerbArray** structure returned in the  _ppMAPIVerbArray_ parameter, the verbs are returned in order of index number; each verb's index is found in its **lVerb** member. Client applications can use the verb array to dynamically build menus, hide or show buttons, and so on. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MFCOutput.cpp  <br/> |_OutputFormInfo  <br/> |MFCMAPI uses the **IMAPIFormInfo::CalcVerbSet** method while writing debug output for form information objects.  <br/> |
   
## See also

#### Reference

[SMAPIVerbArray](smapiverbarray.md)
  
[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

