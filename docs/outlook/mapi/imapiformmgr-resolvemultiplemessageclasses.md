---
title: "IMAPIFormMgrResolveMultipleMessageClasses"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormMgr.ResolveMultipleMessageClasses
api_type:
- COM
ms.assetid: d3cc6658-e46d-42dd-b1ac-65c88cfef8ca
---

# IMAPIFormMgr::ResolveMultipleMessageClasses

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Resolves a group of message classes to their forms within a form container, and returns an array of form information objects for those forms.
  
```cpp
HRESULT ResolveMultipleMessageClasses(
  LPSMESSAGECLASSARRAY pMsgClasses,
  ULONG ulFlags,
  LPMAPIFOLDER pFolderFocus,
  LPSMAPIFORMINFOARRAY FAR * ppfrminfoarray
);
```

## Parameters

 _pMsgClasses_
  
> [in] A pointer to an array that contains the names of the message classes to resolve.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the message classes are resolved. The following flag can be set:
    
MAPIFORM_EXACTMATCH 
  
> Only message class strings that are an exact match should be resolved.
    
MAPIFORM_LOCALONLY
  
> Do not include cached forms.
    
 _pFolderFocus_
  
> [in] A pointer to the folder that contains the form whose message class is being resolved. The  _pFolderFocus_ parameter can be NULL. 
    
 _ppfrminfoarray_
  
> [out] A pointer to a pointer to an array of form information objects. If a form viewer passes NULL in the _pMsgClasses_ parameter, the  _ppfrminfoarray_ parameter contains form information objects for all forms in the container. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Form viewers call the **IMAPIFormMgr::ResolveMultipleMessageClasses** method to resolve a group of message classes to forms within a form container. The array of form information objects returned in  _ppfrminfoarray_ provides further access to each of the forms' properties. 
  
## Notes to callers

To resolve a group of message classes to forms, a form viewer passes in an array of message class names to be resolved. To force the resolution to be exact (that is, to prevent resolution to a base class of the message class when an exactly matching form server is not available) the MAPIFORM_EXACTMATCH flag can be passed in the _ulFlags_ parameter. 
  
Message class names are always ANSI strings, never Unicode.
  
If a message class cannot be resolved to a form, NULL is returned for that message class in the form information array. Therefore, even if the method returns S_OK, form viewers should not work on the assumption that all message classes have been successfully resolved. Instead, form viewers should check the values in the returned array.
  
## See also



[IMAPIFormMgr::ResolveMessageClass](imapiformmgr-resolvemessageclass.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)

