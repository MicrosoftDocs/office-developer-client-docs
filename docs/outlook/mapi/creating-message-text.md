---
title: "Creating message text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 70d1fb24-91a9-4043-8c9d-be1523012e6b
---

# Creating message text

**Applies to**: Outlook 2013 | Outlook 2016 
  
Although some messages are made up of nothing more than a recipient list and a subject line, the content of most messages, specifically IPM.Note messages, includes text. Message text can be plain or formatted and is stored in three properties: **PR\_BODY** ([PidTagBody](pidtagbody-canonical-property.md)), **PR\_HTML** ([PidTagHtml](pidtaghtml-canonical-property.md)), and **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)). 

If your client is plain text-based, set **PR\_BODY**. If you support formatted text in the Rich Text Format (RTF), set either **PR_RTF_COMPRESSED** only or both **PR_RTF_COMPRESSED** and **PR\_BODY**, depending on the message store provider that you are using. When an RTF-aware client is using an RTF-aware message store, it sets **PR_RTF_COMPRESSED** only. When an RTF-aware client is using a non-RTF-aware message store, it sets both properties. If your client supports HTML, set the **PR_HTML** property. 
  
## Determine whether your message store supports Rich Text Format
  
1. Call the message store's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property.
    
2. Check for the STORE_RTF_OK bit. If STORE_RTF_OK is set, the message store provider supports RTF text. If it is not set, the message store provider supports plain text only.
    
## Determine whether your message store supports HTML
  
1. Call the message store's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_STORE_SUPPORT_MASK** property. 
    
2. Check for the STORE_HTML_OK bit. If STORE_HTML_OK is set, the message store provider supports HTML text. 
    
## Set PR\_RTF_COMPRESSED
  
1. Call the message's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_RTF_COMPRESSED** property, specifying IID_IStream as the interface identifier and setting the MAPI_CREATE flag. 
    
2. Call the [WrapCompressedRTFStream](wrapcompressedrtfstream.md) function, passing the STORE_UNCOMPRESSED_RTF flag if the STORE_UNCOMPRESSED_RTF bit is set in the message store's **PR_STORE_SUPPORT_MASK** property. 
    
3. Release the original stream by calling its ** IUnknown::Release ** method. 
    
4. Call either ** IStream::Write ** or **IStream::CopyTo** to write the message text to the stream returned from **WrapCompressedRTFStream**.
    
5. Call the **Commit** and **Release** methods on the stream returned from the **OpenProperty** method. 
    
At this point, if the message store provider supports RTF, you have done all that is required. You can depend on the message store provider to handle synchronizing the message content and formatting and to create the **PR\_BODY** property if necessary. RTF-aware message stores call [RTFSync](rtfsync.md) to handle the synchronization. If the RTF\_SYNC_BODY_CHANGED flag is set to TRUE, the provider will recompute the **PR_BODY** property. 
  
If your message store provider does not support RTF, you must also add non-RTF message content by setting the **PR_BODY** property. 
  
## Set PR_HTML
  
1. Call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_HTML** property with the **IStream** interface. 
    
2. Call **IStream::Write** to write the message text data to the stream returned from **OpenProperty**. 
    
3. Call **IStream::Commit** and **IUnknown::Release** on the stream to commit the changes and free its memory. 
    
## Set PR_BODY
  
1. Call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_BODY** property with the **IStream** interface. 
    
2. Call **IStream::Write** to write the message text data to the stream returned from **OpenProperty**. 
    
3. Call the [RTFSync](rtfsync.md) function to synchronize the text with the formatting. Because this is a new message, set both the RTF_SYNC_RTF_CHANGED and RTF_SYNC_BODY_CHANGED flags to indicate that both the RTF and plain text version of the message text has changed. **RTFSync** will set several related properties that the message store provider requires, such as **PR_RTF_IN_SYNC** ([PidTagRtfInSync](pidtagrtfinsync-canonical-property.md)), and write them to the message.
    
4. Call **IStream::Commit** and **IUnknown::Release** on the stream to commit the changes and free its memory. 
    

