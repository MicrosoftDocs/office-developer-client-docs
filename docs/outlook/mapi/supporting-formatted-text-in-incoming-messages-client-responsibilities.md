---
title: "Supporting Formatted Text in Incoming Messages Client Responsibilities"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 79727700-5ef1-4a29-9ed0-fd46c7de3202
description: "Last modified: July 23, 2011"
 
 
---

# Supporting Formatted Text in Incoming Messages: Client Responsibilities

  
  
**Applies to**: Outlook 
  
As messages are transferred between messaging systems, the MAPI spooler makes sure that the rich text formatting remains synchronized with the message text. The MAPI spooler calls the [RTFSync](rtfsync.md) function from within a wrapped version of the message that it passes to the transport provider. The transport provider saves the changes made to the message by calling the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method and then routes it to the new recipient. 
  
When the recipient's RTF-aware client application opens the message to display the text, it must synchronize the text with the formatting and open either **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) or **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)), depending on which property is available.
  
 **To open a message, RTF-aware clients**
  
1. Call **RTFSync** to synchronize the message text with the formatting if the message store is not RTF-aware. The RTF_SYNC_BODY_CHANGED flag should be passed in the  _ulFlags_ parameter if the **PR_RTF_IN_SYNC** ([PidTagRtfInSync](pidtagrtfinsync-canonical-property.md)) property is missing or set to FALSE. Clients working with RTF-aware message stores need not make the **RTFSync** call because the message store takes care of it. 
    
2. Call [IMAPIProp::SaveChanges](imapiprop-savechanges.md) if the message text has been updated. 
    
3. Call [IMAPIProp::OpenProperty](imapiprop-openproperty.md) to open the **PR_RTF_COMPRESSED** property. If **PR_RTF_COMPRESSED** is not available, you should open the **PR_BODY** property instead to display the message content. 
    
4. Call the [WrapCompressedRTFStream](wrapcompressedrtfstream.md) function to create an uncompressed version of the compressed RTF data, if available. 
    
5. Display the uncompressed RTF data or the plain text data to the user.
    
 **RTFSync** returns a Boolean value that indicates whether or not the message has been updated. If this value returns TRUE, call **SaveChanges** at some point to make the update permanent. The call does not have to be made immediately after **RTFSync** returns. 
  
> [!NOTE]
> Because so many components handle the formatted text before you receive it, there is the possibility of corruption. This corruption could come from the message store provider, a third party application, a gateway, or a transmission error. 
  

