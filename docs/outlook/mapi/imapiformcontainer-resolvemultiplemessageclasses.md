---
title: "IMAPIFormContainerResolveMultipleMessageClasses"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormContainer.ResolveMultipleMessageCla
api_type:
- COM
ms.assetid: f18c2dd1-366f-48b4-b335-ebbc0651f467
description: "Last modified: March 09, 2015"
---

# IMAPIFormContainer::ResolveMultipleMessageClasses

  
  
**Applies to**: Outlook 
  
Resolves a group of message classes to their forms in a form container and returns an array of form information objects for those forms.
  
```cpp
HRESULT ResolveMultipleMessageClasses(
  LPSMESSAGECLASSARRAY pMsgClassArray,
  ULONG ulFlags,
  LPSMAPIFORMINFOARRAY FAR * ppfrminfoarray
);
```

## Parameters

 _pMsgClassArray_
  
> [in] A pointer to an array that contains the names of the message classes to resolve. Message class names are always ANSI strings, never Unicode.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the message classes are resolved. The following flag can be set:
    
MAPIFORM_EXACTMATCH 
  
> Only message class strings that are an exact match should be resolved.
    
 _ppfrminfoarray_
  
> [out] A pointer to a pointer to an array of form information objects. If a client application passes NULL in the  _pMsgClassArray_ parameter, the  _ppfrminfoarray_ parameter contains form information objects for all forms in the container. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Client applications call the **IMAPIFormContainer::ResolveMultipleMessageClasses** method to resolve a group of message classes to forms within a form container. The array of form information objects returned in the  _ppfrminfoarray_ parameter provides further access to each of the forms' properties. 
  
## Notes to callers

To resolve a group of message classes to forms, pass in an array of message class names to be resolved. To force the resolution to be exact (that is, to prevent resolution to a base class of the message class), the MAPIFORM_EXACTMATCH flag can be passed in the  _ulFlags_ parameter. 
  
If a message class cannot be resolved to a form, NULL is returned for that message class in the form information array. Therefore, even if the method returns S_OK, do not assume that all message classes have been successfully resolved. Instead, check the values in the returned array.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FormContainerDlg.cpp  <br/> |CFormContainerDlg::OnResolveMultipleMessageClasses  <br/> |MFCMAPI uses the **IMAPIFormContainer::ResolveMultipleMessageClasses** method to locate a form that is associated with a set of message classes.  <br/> |
   
## See also



[IMAPIFormContainer::ResolveMessageClass](imapiformcontainer-resolvemessageclass.md)
  
[IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

