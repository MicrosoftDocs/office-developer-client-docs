---
title: "Rendering an Attachment in Plain Text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 72b447e9-b4f2-4557-baf5-0afefe463749
description: "Last modified: July 23, 2011"
 
 
---

# Rendering an Attachment in Plain Text

  
  
**Applies to**: Outlook 
  
To render an attachment in a message with plain text, retrieve the attachment's **PR_RENDERING_POSITION** ( [PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md)) property and apply it to the data in the **PR_ATTACH_RENDERING** ( [PidTagAttachRendering](pidtagattachrendering-canonical-property.md)) property. There are two ways to retrieve **PR_RENDERING_POSITION**:
  
- Open the attachment by calling the message's **IMessage::OpenAttach** method and then ask for the **PR_RENDERING_POSITION** property by calling the attachment's **IMAPIProp::GetProps** method. For more information, see [IMessage::OpenAttach](imessage-openattach.md) and [IMAPIProp::GetProps](imapiprop-getprops.md).
    
- Call the message's **IMessage::GetAttachmentTable** method to access its attachment table and retrieve the column that holds the **PR_RENDERING_POSITION** property. This way is always preferable. For more information, see [IMessage::GetAttachmentTable](imessage-getattachmenttable.md).
    
Keep in mind that many RTF-aware message stores do not calculate **PR_RENDERING_POSITION** until a client requests the **PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md)) property of a message. Until that time, **PR_RENDERING_POSITION** usually represents an approximate value. Message store providers are allowed to supply clients with an approximate value to enhance performance. 
  
The rendering for a file or binary attachment is stored in its **PR_ATTACH_RENDERING** property. You have the choice of retrieving **PR_ATTACH_RENDERING** in the same ways as you retrieved **PR_RENDERING_POSITION**: directly from the attachment or from the attachment table. For **PR_ATTACH_RENDERING**, the first strategy, although more time-consuming, is safer. Because some message store providers truncate their table columns to 255 bytes, or in a few cases 510 bytes, it is difficult to be sure that the **PR_ATTACH_RENDERING** column contains the complete rendering. When retrieving the property directly from the attachment, it will always be complete. 
  
Neither OLE nor message attachments set **PR_ATTACH_RENDERING**. Instead, rendering information for OLE 1 attachments is stored in the message text stream. For OLE 2 attachments, it is stored in a special child stream of the storage object. Rendering information for message attachments is available through the form manager. 
  
 **To retrieve the rendering for a message attachment**
  
1. Use the message class of the message to access the form manager.
    
2. Access the form manager's **PR_MINI_ICON** property. For more information, see **PR_MINI_ICON** ( [PidTagMiniIcon](pidtagminiicon-canonical-property.md)).
    

