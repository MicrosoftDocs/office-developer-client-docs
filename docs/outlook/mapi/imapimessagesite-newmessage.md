---
title: "IMAPIMessageSiteNewMessage"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIMessageSite.NewMessage
api_type:
- COM
ms.assetid: ce6b6e6c-7f22-43c2-8182-90cf6db93844
description: "Last modified: March 09, 2015"
---

# IMAPIMessageSite::NewMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a new message.
  
```cpp
HRESULT NewMessage(
  ULONG fComposeInFolder,
  LPMAPIFOLDER pFolderFocus,
  LPPERSISTMESSAGE pPersistMessage,
  LPMESSAGE FAR * ppMessage,
  LPMAPIMESSAGESITE FAR * ppMessageSite,
  LPMAPIVIEWCONTEXT FAR * ppViewContext
);
```

## Parameters

 _fComposeInFolder_
  
> [in] Indicates in which folder the message should be composed. If the variable is FALSE, the  _pFolderFocus_ parameter is ignored and the form viewer can compose the message in any folder. If the variable is TRUE and NULL is passed in the _pFolderFocus_ parameter, the message is composed in the current folder. If the variable is TRUE and a non-NULL value is passed in  _pFolderFocus_, the message is composed in the folder pointed to by  _pFolderFocus_.
    
 _pFolderFocus_
  
> [in] A pointer to the folder where the new message is created.
    
 _pPersistMessage_
  
> [in] A pointer to the form object for the new form.
    
 _ppMessage_
  
> [out] A pointer to a pointer to the new message.
    
 _ppMessageSite_
  
> [out] A pointer to a pointer to a message site object for the new message.
    
 _ppViewContext_
  
> [out] A pointer to a pointer to a view context that is appropriate for passing to a new form with the new message. If the form implements its own view context, NULL can be passed in the _ppViewContext_ parameter. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Form objects call the **IMAPIMessageSite::NewMessage** method to create a new message. The form uses **NewMessage** to get a new message and the associated message site from its view. It can then modify the new message. 
  
You can also obtain an associated view context by passing in a non-NULL value in the _ppViewContext_ parameter. This view context can be used directly, or it can be aggregated and passed to the new message. If a complete implementation is required, pass NULL in  _ppViewContext_.
  
For a list of interfaces related to form servers, see [MAPI Form Interfaces](mapi-form-interfaces.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::NewMessage  <br/> |MFCMAPI uses the **IMAPIMessageSite::NewMessage** method to create a new message, instantiate a new form viewer, and call **SetPersist** to set the message on the form viewer. Finally, it returns the form viewer as the message site.  <br/> |
   
## See also



[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)
  
[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Form Interfaces](mapi-form-interfaces.md)

