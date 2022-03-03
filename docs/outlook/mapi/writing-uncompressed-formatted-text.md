---
title: "Writing Uncompressed Formatted Text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c78d4d00-bc31-4d0b-8af0-dd0b8f3febfe
 
 
---

# Writing Uncompressed Formatted Text

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When preparing to send a message with formatted text, either set the message's **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property to compressed or uncompressed text. Writing compressed text in the **PR_RTF_COMPRESSED** property is a very CPU intensive operation and can dramatically affect performance. 
  
To improve the performance of sending formatted messages, either:
  
- Upgrade the CPU, a solution that is not always plausible.
    
    - Or -
    
- Write uncompressed text in the **PR_RTF_COMPRESSED** property. 
    
The procedure for setting **PR_RTF_COMPRESSED** with uncompressed text is the same as for setting it with compressed text, with one exception. When calling [WrapCompressedRTFStream](wrapcompressedrtfstream.md), set the STORE_UNCOMPRESSED_RTF flag in the _ulFlags_ parameter. Setting uncompressed text has the disadvantage in that it increases the size of messages. 
  

