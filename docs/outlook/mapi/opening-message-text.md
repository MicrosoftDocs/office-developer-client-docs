---
title: "Opening message text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e37fc9d8-433b-41b4-84f2-42a952063f35
description: "Last modified: July 23, 2011"
---

# Opening message text

**Applies to**: Outlook 
  
The text of a message is stored either in its **PR\_BODY** property or **PR\_RTF\_COMPRESSED** property. For more information, see **PR\_BODY** ([PidTagBody](pidtagbody-canonical-property.md)), **PR\_HTML** ([PidTagHtml](pidtaghtml-canonical-property.md)), and **PR\_RTF\_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)). 

If you support the Rich Text Format (RTF), open **PR\_RTF_COMPRESSED**. If you do not support RTF, open **PR\_BODY**. Because the text of a message can be large regardless of whether or not it is formatted, use **IMAPIProp::OpenProperty** to open these properties. For more information, see [IMAPIProp::OpenProperty](imapiprop-openproperty.md).
  
### To display formatted message text
  
1. If you are using a non-RTF aware message store, as indicated by the absence of the STORE_RTF_OK flag in the store's **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property:
    
    1. Call the message's **IMAPIProp::GetProps** method to retrieve the **PR_RTF_IN_SYNC** property. For more information, see [IMAPIProp::GetProps](imapiprop-getprops.md) and **PR_RTF_IN_SYNC** ([PidTagRtfInSync](pidtagrtfinsync-canonical-property.md)).
        
    2. Call RTFSync to synchronize the message's PR_BODY property with the **PR_RTF_COMPRESSED** property. For more information, see [RTFSync](rtfsync.md), **PR_BODY**, and **PR_RTF_COMPRESSED**. Pass the RTF_SYNC_BODY_CHANGED flag if the call to retrieve **PR_RTF_IN_SYNC** failed because the property does not exist or it is set to FALSE. 
        
    3. If **RTFSync** returned TRUE — indicating that changes were made — call the message's **IMAPIProp::SaveChanges** method to permanently store them. For more information, see [IMAPIProp::SaveChanges](imapiprop-savechanges.md).
    
2. Regardless of whether or not you are using an RTF-aware message store:
    
    1. Call **IMAPIProp::OpenProperty** to open the **PR_RTF_COMPRESSED** property. For more information, see [IMAPIProp::OpenProperty](imapiprop-openproperty.md) and **PR_RTF_COMPRESSED**.
        
    2. If **PR_RTF_COMPRESSED** is not available, call **OpenProperty** to open the **PR_BODY** property. 
        
    3. Call the **WrapCompressedRTFStream** function to create an uncompressed version of the compressed RTF data, if available. For more information, see [WrapCompressedRTFStream](wrapcompressedrtfstream.md).
        
    4. Copy the formatted text from the stream to the appropriate place in the message form. 
    
### To display plain message text
  
1. Call the message's **IMAPIProp::GetProps** method to retrieve the **PR_BODY** property. For more information, see [IMAPIProp::GetProps](imapiprop-getprops.md).
    
2. If **GetProps** returns either PT_ERROR for the property type in the property value structure or MAPI_E_NOT_ENOUGH_MEMORY, call the message's **IMAPIProp::OpenProperty** method. Pass **PR_BODY** as the property tag and IID_IStream as the interface identifier. For more information, see [IMAPIProp::OpenProperty](imapiprop-openproperty.md).
    
3. Copy the plain text from the stream to the appropriate place in the message form. 
    

