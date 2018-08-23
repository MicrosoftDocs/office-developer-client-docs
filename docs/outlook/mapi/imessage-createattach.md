---
title: "IMessageCreateAttach"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.IMessage::CreateAttach
api_type:
- COM
ms.assetid: 01711aca-c598-438c-88d7-0719b6691e34
description: "Last modified: July 23, 2011"
---

# IMessage::CreateAttach

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a new attachment.
  
```cpp
HRESULT CreateAttach(
LPCIID lpInterface,
ULONG ulFlags,
ULONG FAR * lpulAttachmentNum,
LPATTACH FAR * lppAttach
);
```

## Parameters

 _lpInterface_
  
> [in] Pointer to the interface identifier (IID) representing the interface to be used to access the message. Passing NULL results in the message's standard interface, or **IMessage**, being returned. 
    
 _ulFlags_
  
> [in] Bitmask of flags that controls how the attachment is created. The following flag can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **CreateAttach** to return successfully, possibly before the attachment is fully accessible to the calling client. If the attachment is not accessible, making a subsequent call to it can result in an error. 
    
 _lpulAttachmentNum_
  
> [out] Pointer to an index number identifying the newly created attachment. This number is valid only when the message is open and is the basis for the attachment's **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property.
    
 _lppAttach_
  
> [out] Pointer to a pointer to the open attachment object.
    
## Return value

S_OK 
  
> The attachment was successfully created.
    
## Remarks

The **IMessage::CreateAttach** method creates a new attachment on a message. The new attachment and any properties that are set for it, are not available until a client has called both the attachment's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method and the message's **IMAPIProp::SaveChanges** method. 
  
The attachment number pointed to by  _lpulAttachmentNum_ is unique and valid only within the context of the message. That is, two attachments in two different messages can have the same number while two attachments in the same message cannot. 
  
## See also



[IMessage : IMAPIProp](imessageimapiprop.md)

