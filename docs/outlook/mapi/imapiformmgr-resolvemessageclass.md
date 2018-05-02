---
title: "IMAPIFormMgrResolveMessageClass"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.ResolveMessageClass
api_type:
- COM
ms.assetid: c2af7516-3a97-4422-874d-b1e3a0d4f316
description: "Last modified: July 23, 2011"
---

# IMAPIFormMgr::ResolveMessageClass

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Resolves a message class to its form within a form container, and returns a form information object for that form.
  
```
HRESULT ResolveMessageClass(
  LPCSTR szMsgClass,
  ULONG ulFlags,
  LPMAPIFOLDER pFolderFocus,
  LPMAPIFORMINFO FAR * ppResult
);
```

## Parameters

 _szMsgClass_
  
> [in] A string that names the message class being resolved.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the message class is resolved. The following flag can be set:
    
MAPIFORM_EXACTMATCH 
  
> Only message class strings that are an exact match should be resolved.
    
 _pFolderFocus_
  
> [in] A pointer to the folder that contains the message being resolved. The  _pFolderFocus_ parameter can be NULL. 
    
 _ppResult_
  
> [out] A pointer to a pointer to a returned form information object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NOT_FOUND 
  
> The message class passed in the  _szMsgClass_ parameter does not match the message class for any form in the form library. 
    
## Remarks

Form viewers call the **IMAPIFormMgr::ResolveMessageClass** method to resolve a message class to its form within a form container. The form information object returned in the  _ppResult_ parameter provides further access to the properties of the form that has the given message class. 
  
## Notes to Callers

To resolve a message class to a form, a form viewer passes in the name of the message class to be resolved, such as " `IPM.HelpDesk.Software`". To force the resolution to be exact (that is, to prevent resolution to a base class of the message class when an exactly matching form server is not available), the MAPIFORM_EXACTMATCH flag can be passed in the  _ulFlags_ parameter. If the  _pFolderFocus_ parameter is NULL, the message-class resolution process does not search a folder container. 
  
The order of the containers searched depends on the implementation of the form library provider. The default form library provider searches first the local container, then the folder container for the passed-in folder, the personal form container and, finally, the organization container.
  
Message class names are always ANSI strings, never Unicode.
  
The class identifier for the resolved message class is returned as part of the form information object. A form viewer should not work on the assumption that the class identifier exists in the OLE library until after the form viewer has called either the [IMAPIFormMgr::PrepareForm](imapiformmgr-prepareform.md) method or the [IMAPIFormMgr::CreateForm](imapiformmgr-createform.md) method. 
  
## See also

#### Reference

[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)
  
[IMAPIFormMgr::CreateForm](imapiformmgr-createform.md)
  
[IMAPIFormMgr::PrepareForm](imapiformmgr-prepareform.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)

