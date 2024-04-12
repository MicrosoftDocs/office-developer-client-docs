---
title: "IMAPIFormContainerResolveMessageClass"
description: "IMAPIFormContainerResolveMessageClass resolves a message class to its form in a form container and returns a form information object for that form."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormContainer.ResolveMessageClass
api_type:
- COM
ms.assetid: 9ce13f11-5787-4ea5-a84f-b1e3824529ee
---

# IMAPIFormContainer::ResolveMessageClass

**Applies to**: Outlook 2013 | Outlook 2016
  
Resolves a message class to its form in a form container and returns a form information object for that form.
  
```cpp
HRESULT ResolveMessageClass(
  LPCSTR szMessageClass,
  ULONG ulFlags,
  LPMAPIFORMINFO FAR * ppforminfo
);
```

## Parameters

 _szMessageClass_
  
> [in] A string that names the message class being resolved. Message class names are always ANSI strings, never Unicode.

 _ulFlags_
  
> [in] A bitmask of flags that controls how the message class is resolved. The following flag can be set:

MAPIFORM_EXACTMATCH
  
> Only message class strings that are an exact match should be resolved.

 _ppforminfo_
  
> [out] A pointer to a pointer to the returned form information object.

## Return value

S_OK
  
> The call succeeded and has returned the expected value or values.

MAPI_E_NOT_FOUND
  
> The message class passed in the _szMessageClass_ parameter does not match the message class for any form in the form container.

## Remarks

Client applications call the **IMAPIFormContainer::ResolveMessageClass** method to resolve a message class to a form within a form container. The form information object returned in the _ppforminfo_ parameter provides further access to the properties of the form with the given message class.
  
## Notes to callers

To resolve a message class to a form, pass in the name of the message class to be resolved (for example, `IPM.HelpDesk.Software`). To force the resolution to be exact (that is, to prevent resolution to a base class of the message class), the MAPIFORM_EXACTMATCH flag can be passed in the _ulFlags_ parameter.
  
The class identifier for the resolved message class is returned as part of the form information object. Do not assume that the class identifier exists in the OLE library until after you call either the [IMAPIFormMgr::PrepareForm](imapiformmgr-prepareform.md) or [IMAPIFormMgr::CreateForm](imapiformmgr-createform.md) method.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FormContainerDlg.cpp  <br/> |CFormContainerDlg::OnResolveMessageClass  <br/> |MFCMAPI uses the **IMAPIFormContainer::ResolveMessageClass** method to locate a form that is associated with a message class. |

## See also

[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)
  
[IMAPIFormMgr::CreateForm](imapiformmgr-createform.md)
  
[IMAPIFormMgr::PrepareForm](imapiformmgr-prepareform.md)
  
[IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md)
