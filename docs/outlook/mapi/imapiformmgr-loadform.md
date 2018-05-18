---
title: "IMAPIFormMgrLoadForm"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.LoadForm
api_type:
- COM
ms.assetid: 5ca500c3-c737-45a5-b0fc-473b75c1d68d
description: "Last modified: March 09, 2015"
---

# IMAPIFormMgr::LoadForm

  
  
**Applies to**: Outlook 
  
Starts a form to open an existing message.
  
```cpp
HRESULT LoadForm(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPCSTR lpszMessageClass,
  ULONG ulMessageStatus,
  ULONG ulMessageFlags,
  LPMAPIFOLDER pFolderFocus,
  LPMAPIMESSAGESITE pMessageSite,
  LPMESSAGE pmsg,
  LPMAPIVIEWCONTEXT pViewContext,
  REFIID riid,
  LPVOID FAR * ppvObj
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator that is displayed while the form is opened. The  _ulUIParam_ parameter is ignored unless the MAPI_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the form is opened. The following flags can be set:
    
MAPI_DIALOG 
  
> Displays a user interface to provide status or prompt the user for more information. If this flag is not set, no user interface is displayed.
    
MAPIFORM_EXACTMATCH 
  
> Only message class strings that are an exact match should be resolved.
    
 _lpszMessageClass_
  
> [in] A pointer to a string that names the message class of the message to be loaded. If NULL is passed in the  _lpszMessageClass_ parameter, the message class is determined from the message pointed to by the  _pmsg_ parameter. 
    
 _ulMessageStatus_
  
> [in] A bitmask of client-defined or provider-defined flags copied from the **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property of the message that provides information about the state of the message. The  _ulMessageStatus_ parameter must be set if  _lpszMessageClass_ is non-NULL; otherwise,  _ulMessageStatus_ is ignored. 
    
 _ulMessageFlags_
  
> [in] A pointer to a bitmask of flags copied from the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of the message that indicates the current state of the message. The  _ulMessageFlags_ parameter must be set if  _lpszMessageClass_ is non-NULL; otherwise,  _ulMessageFlags_ is ignored. 
    
 _pFolderFocus_
  
> [in] A pointer to the folder that directly contains the message. The  _pFolderFocus_ parameter can be NULL if such a folder does not exist (for example, if the message is embedded in another message). 
    
 _pMessageSite_
  
> [in] A pointer to the message site of the message.
    
 _pmsg_
  
> [in] A pointer to the message.
    
 _pViewContext_
  
> [in] A pointer to the view context for the message. The  _pViewContext_ parameter can be NULL. 
    
 _riid_
  
> [in] The interface identifier (IID) of the interface to be used for the returned form object. The  _riid_ parameter must not be NULL. 
    
 _ppvObj_
  
> [out] A pointer to a pointer to the returned interface.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_INTERFACE 
  
> The form does not support the requested interface.
    
MAPI_E_NOT_FOUND 
  
> The message class passed in  _lpszMessageClass_ does not match the message class for any form in the form library. 
    
## Remarks

Form viewers call the **IMAPIFormMgr::LoadForm** method to open a form for an existing message. **LoadForm** opens the form object, loads the message into the form object, sets up the appropriate view context, if necessary, and returns the requested interface for the form object. 
  
The  _pFolderFocus_ parameter points to the folder that contains the message. If the message is embedded in another message,  _pFolderFocus_ should be NULL. 
  
## Notes to implementers

If NULL is passed in  _lpszMessageClass_, the implementation obtains the message's message class, status, and flags from the message's **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)), **PR_MSG_STATUS** and **PR_MESSAGE_FLAGS** properties. If a message class string is provided in  _lpszMessageClass_, the implementation must use the values in  _ulMessageStatus_ and  _ulMessageFlags_.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFormFunctions.cpp  <br/> |OpenMessageNonModal  <br/> |MFCMAPI uses the **IMAPIFormMgr::LoadForm** method to load a form before displaying it.  <br/> |
   
## See also



[PidTagMessageClass Canonical Property](pidtagmessageclass-canonical-property.md)
  
[PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md)
  
[PidTagMessageStatus Canonical Property](pidtagmessagestatus-canonical-property.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

