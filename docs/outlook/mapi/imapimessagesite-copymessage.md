---
title: "IMAPIMessageSiteCopyMessage"
description: "Describes the syntax, parameters, and return value of IMAPIMessageSiteCopyMessage, which copies the current message to a folder."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIMessageSite.CopyMessage
api_type:
- COM
ms.assetid: d4e18483-409a-4d81-91dc-f4aec29a82bb
---

# IMAPIMessageSite::CopyMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies the current message to a folder.
  
```cpp
HRESULT CopyMessage(
  LPMAPIFOLDER pFolderDestination
);
```

## Parameters

 _pFolderDestination_
  
> [in] A pointer to the folder where the message is to be copied.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_SUPPORT 
  
> The operation is not supported by this message site.
    
## Remarks

Form objects call the **IMAPIMessageSite::CopyMessage** method to copy the current message to a new folder. **CopyMessage** does not change the message currently being displayed to the user, and no interface for the newly created message is returned to the form. 
  
## Notes to implementers

A typical implementation of the **CopyMessage** method performs the following tasks: 
  
1. Creates a new message for the current message to be copied to.
    
2. Calls the [IPersistMessage::Save](ipersistmessage-save.md) method with a pointer to the new message in the _pMessage_ parameter and FALSE in the _fSameAsLoad_ parameter. 
    
3. Calls the [IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md) method, passing NULL in the _pMessage_ parameter. 
    
4. Calls the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method on the new message. 
    
For a list of interfaces that are related to form servers, see [MAPI Form Interfaces](mapi-form-interfaces.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::CopyMessage  <br/> |Not implemented. |
   
## See also



[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IPersistMessage::Save](ipersistmessage-save.md)
  
[IPersistMessage::SaveCompleted](ipersistmessage-savecompleted.md)
  
[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Form Interfaces](mapi-form-interfaces.md)

