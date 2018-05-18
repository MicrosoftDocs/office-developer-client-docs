---
title: "Supporting Formatted Text Message Store Responsibilities"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a97993c2-52e4-4b71-ac03-2c02d82447d8
description: "Last modified: March 09, 2015"
 
 
---

# Supporting Formatted Text: Message Store Responsibilities

  
  
**Applies to**: Outlook 
  
Message store providers use the **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property to publish whether or not they can handle Rich Text Format (RTF), HTML text and, if they are RTF-aware, whether they store the formatted text in a compressed or uncompressed format. Message store providers indicate that they are RTF-aware by setting the STORE_RTF_OK bit and that they store the formatted text in an uncompressed form by setting the STORE_UNCOMPRESSED_RTF bit. Message store providers indicate they are HTML-aware by setting the STORE_HTML_OK bit.
  
While it is important for an RTF-aware client to check for the STORE_RTF_OK bit to determine whether or not a message store supports RTF, it is not necessary for a client to be concerned with the format of an RTF-aware store's formatted text. 
  
All message stores must support non-RTF-aware clients. A non-RTF-aware message store must delete the **PR_RTF_IN_SYNC** ([PidTagRtfInSync](pidtagrtfinsync-canonical-property.md)) property during a call to the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method if a client has changed **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) without updating either **PR_RTF_IN_SYNC** or **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)). Deleting **PR_RTF_IN_SYNC** causes the **PR_RTF_COMPRESSED** property to be recomputed from the **PR_BODY** property the next time an RTF-aware client calls [RTFSync](rtfsync.md). 
  
Most RTF-aware message stores are not given the message text by clients; it must be computed on request. Because this computation is time consuming and expensive, clients should use **PR_RTF_COMPRESSED** whenever possible. To compute the **PR_BODY** property, the message store provider must uncompress the contents of the **PR_RTF_COMPRESSED** property and remove the rich text formatting. Clients that do not support the **PR_RTF_COMPRESSED** property require this computation to take place for every message. 
  
When copying messages, message store providers that do not use the **IMAPISupport::DoCopyProps** or **IMAPISupport::DoCopyTo** methods run the risk of creating a message with no content if their implementation excludes the **PR_BODY** property and relies on **PR_RTF_COMPRESSED**. It is possible for the data in the **PR_RTF_COMPRESSED** property to be corrupt. Before excluding either of these message content properties in the copy operation, check for corruption as follows: 
  
1. If the value of **PR_RTF_COMPRESSED** is not larger than the compressed RTF, the property is corrupt. 
    
2. If the magic value in the RTF header is not  _dwMagicCompressedRTF_ or  _dwMagicUncompressedRTF_, the property is corrupt.
    
Message store providers using the support methods need not be concerned with implementing a check for **PR_RTF_COMPRESSED** corruption; MAPI ensures that the appropriate properties exist and are valid. 
  
There are three different levels of RTF support that message store providers can implement; MAPI recommends that RTF-aware message store providers implement their support at the middle or highest level. All RTF-aware message store providers take care of generating **PR_BODY** from the data included in **PR_RTF_COMPRESSED** on outgoing messages and make a call to **RTFSync** to synchronize text and formatting on incoming messages. 
  
The differences between these three levels are described in the following table. 
  
|**Level of support**|**Description**|
|:-----|:-----|
|Low  <br/> |Message store provider calls **RTFSync** whenever changes are saved to a message and extracts the data for the **PR_BODY** property from **PR_RTF_COMPRESSED** rather than requiring clients to set it. Both **PR_BODY** and **PR_RTF_COMPRESSED** are stored.  <br/> |
|Middle  <br/> |Message store provider stores only the **PR_RTF_COMPRESSED** property, computing **PR_BODY** when necessary.  <br/> |
|High  <br/> |Message store provider stores neither **PR_BODY** or the auxiliary RTF properties. **RTFSync** is called when the message text has changed and the formatting remains unchanged or when a new message is downloaded by a transport provider.  <br/> |
   

