---
title: "MAPI Attachments"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 6e6c6ad9-1e07-4234-a5ef-18020d7ce468
description: "Last modified: July 23, 2011"
---

# MAPI Attachments

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Some message store providers enable clients to associate added information in the form of files, OLE objects, messages, or binary data with messages. This added information is called a message's attachment. Because attachments are created, maintained, and accessed only through their messages, they are considered message subobjects. Rather than having an entry identifier for access, attachments have a sequential number known as an attachment number. This number uniquely identifies the attachment within its message, but not necessarily within the message store. Two different messages can have different attachments with the same attachment number. Attachment numbers are only valid as long as the message is open and are stored in the **PR_ATTACH_NUM** ( [PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property.
  
To access summary information about all of a message's attachments, clients retrieve its attachment table. The attachment table includes information that clients can use to access an attachment directly, such as its attachment number and record key. Clients can retrieve an attachment table by:
  
- Calling **IMessage::GetAttachmentTable**. For more information, see [IMessage::GetAttachmentTable](imessage-getattachmenttable.md).
    
- Calling **IMAPIProp::OpenProperty**. For more information, see [IMAPIProp::OpenProperty](imapiprop-openproperty.md).
    
Message store providers are expected to support both of these approaches. The **OpenProperty** approach requires that the caller specify IID_IMAPITable as the interface identifier and **PR_MESSAGE_ATTACHMENTS** ( [PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) as the property tag. **PR_MESSAGE_ATTACHMENTS** is a table object property that represents a message's attachment table. Message store providers are required to set **PR_MESSAGE_ATTACHMENTS** for each message and include it in the array of property tags returned from the **IMAPIProp::GetPropList** method. For more information, see [IMAPIProp::GetPropList](imapiprop-getproplist.md).
  
 **PR_MESSAGE_ATTACHMENTS** can be used: 
  
- With **IMAPIProp::OpenProperty** to access an attachment or recipient table. 
    
- With **IMAPIProp::CopyTo** or **IMAPIProp::CopyProps** to exclude or include attachments when copying. For more information, see [IMAPIProp::CopyTo](imapiprop-copyto.md) and [IMAPIProp::CopyProps](imapiprop-copyprops.md).
    
- In a subobject restriction to indicate that the child restriction should apply to attachments.
    
For more information, see [Attachment Tables](attachment-tables.md).
  

