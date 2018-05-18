---
title: "Supporting Message Attachments for Message Store Providers"
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d5fabc40-71e8-4afa-9846-533da605ce6c
description: "Last modified: December 07, 2015"
 
 
---

# Supporting Message Attachments for Message Store Providers

 
  
**Applies to**: Outlook 
  
Your message store provider does not need to support message attachments. However, many client applications expect to be able to add attachments to messages. If your message store will be used to create or store IPM.Note messages, then you should support message attachments. Default message store providers should also support message attachments. For more information, see [MAPI Message Classes](mapi-message-classes.md), and [Default Message Stores](default-message-stores.md).
  
There are five types of attachments that MAPI supports: file attachments, data attachments, message attachments, OLE object attachments, and links. The requirements for supporting each type are different. Clients differentiate between the two types of attachments by means of the **PR_ATTACH_METHOD** ([PidTagAttachMethod](pidtagattachmethod-canonical-property.md)) property on attachment objects.
  
Supporting attachments means implementing the [IAttach : IMAPIProp](iattachimapiprop.md) interface. The **IAttach** interface has no methods of its own; it has only methods that are inherited from the [IMAPIProp](imapipropiunknown.md) interface. Because your message store provider must already implement properties for message objects, this greatly simplifies the task of supporting attachments. Implementing **IAttach** basically means providing a way for clients to access a table of properties for particular attachments on messages. 
  
Data attachments are simply attachments for which the contents of the attachment are stored directly in an attachment's **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) property. Data attachments exist primarily to allow clients to attach files to a message when the sender and the recipient of the message do not have access to a common file server. For more information, see the **PR_ATTACH_METHOD** ([PidTagAttachMethod](pidtagattachmethod-canonical-property.md)) property.
  
Message attachments are attachments for which the attachment subobject is another [IMessage : MAPIProp](imessageimapiprop.md) object. Because message store providers already support the **IMessage** interface, supporting message attachments is not difficult. 
  
Supporting OLE object attachments means implementing the OLE **IStorage**, **IStream**, and **IStreamDocfile** interfaces. Your message store provider must be able to convert OLE object data stored in the message into an active OLE object when a client opens the object. 
  
Links come in two types: links to files and links to other messages. Links to files use the ATTACH_BY_REF_ONLY value for the **PR_ATTACH_METHOD** property along with **PR_ATTACH_PATHNAME** ([PidTagAttachPathname](pidtagattachpathname-canonical-property.md)) or **PR_ATTACH_LONG_PATHNAME** ([PidTagAttachLongPathname](pidtagattachlongpathname-canonical-property.md)) to specify the location of a file.
  
How one implements links to messages may depend on aspects of the local messaging system and, as such, cannot be fully documented here. For example, sending a link to a message that is stored on a server-based message store is typically just a matter of sending the entry identifier of the linked message, providing that both the sender and recipient have access to that server. Other messaging system configurations present other requirements and challenges for implementing links to messages.
  
## See also



[Message Store Features](message-store-features.md)

