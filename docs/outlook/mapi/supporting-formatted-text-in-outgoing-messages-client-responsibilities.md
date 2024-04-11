---
title: "Supporting Formatted Text in Outgoing Messages Client Responsibilities"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 7238b1a9-01ed-46a0-a625-26763323317d
 
 
---

# Supporting Formatted Text in Outgoing Messages: Client Responsibilities

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Client applications set the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property, the **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property, or the **PR_HTML** ([PidTagHtml](pidtaghtml-canonical-property.md)) property for an outgoing message. Clients that support only plain text set only the **PR_BODY** property. Rich Text Format (RTF)-aware clients might set both **PR_BODY** and **PR_RTF_COMPRESSED** properties, or only **PR_RTF_COMPRESSED**, depending on the message store provider being used. HTML-aware clients set the **PR_HTML** property. 
  
It is important for a client to check its message store's **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property to determine whether the store supports RTF. If the message store is not RTF-aware, an RTF-aware client sets both the **PR_BODY** and **PR_RTF_COMPRESSED** properties for each outgoing message. 
  
If the message store is RTF-aware, only the **PR_RTF_COMPRESSED** property needs to be set. 
  
 **To set PR_RTF_COMPRESSED and ensure that the synchronization process occurs as necessary, RTF-aware clients**
  
1. Call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_RTF_COMPRESSED** property, setting both the MAPI_CREATE and MAPI_MODIFY flags. MAPI_CREATE ensures that any new data replaces any old data and MAPI_MODIFY enables you to make those replacements. 
    
2. Call the [WrapCompressedRTFStream](wrapcompressedrtfstream.md) function, passing STORE_UNCOMPRESSED_RTF if the message store sets the STORE_UNCOMPRESSED_RTF bit in its **PR_STORE_SUPPORT_MASK** property, to get an uncompressed version of the **PR_RTF_COMPRESSED** stream returned from **OpenProperty**.
    
3. Write the message text data to the uncompressed stream returned from **WrapCompressedRTFStream**.
    
4. Commit and release both the uncompressed and compressed streams.
    
At this point, if the message store provider supports RTF, you have done all that is required. You can depend on the message store provider to handle the synchronization process and the creation of the **PR_BODY** property, if necessary. However, if the message store provider does not support RTF, you must call the [RTFSync](rtfsync.md) function to synchronize the text with the formatting, setting the RTF_SYNC_RTF_CHANGED flag. 
  

