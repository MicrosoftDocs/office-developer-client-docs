---
title: "Supporting Formatted Text Rendering Attachments"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 68abe85b-5dc0-40d0-8917-30ea002aa816
description: "Last modified: July 23, 2011"
 
 
---

# Supporting Formatted Text: Rendering Attachments

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A client application that cares about where in a message its attachments are rendered sets the **PR_RENDERING_POSITION** ([PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md)) property for these attachments during message composition. A client that does not care about rendering placement leaves this property unset.
  
When a client opens a message with attachments, it attempts to retrieve each attachment's **PR_RENDERING_POSITION** property to determine where in the message text the attachment should be rendered. A client can use one of the following methods to retrieve **PR_RENDERING_POSITION**:
  
- [IMAPIProp::GetProps](imapiprop-getprops.md) on the open attachment to retrieve the **PR_RENDERING_POSITION** property. 
    
- [IMessage::GetAttachmentTable](imessage-getattachmenttable.md) on the open message to retrieve its attachment table. **PR_RENDERING_POSITION** is a required column in all attachment tables. This is the preferred method because it results in better performance. 
    
RTF-aware message stores can choose whether to return an accurate or approximate value for **PR_RENDERING_POSITION**. Because message stores recalculate an attachment's **PR_RENDERING_POSITION** value when asked for the message's **PR_BODY** property, some RTF-aware message stores only guarantee the accuracy of rendering positions when a client asks first for **PR_BODY**. RTF-aware message stores are allowed to provide clients with approximate rendering position values to enhance performance. Providing an approximate rather than an accurate rendering position saves time and is sufficient for most situations. 
  
RTF-aware message stores should base their approximation on the value specified by the client responsible for creating the attachment. Although all clients should set **PR_RENDERING_POSITION**, message store providers should be prepared to deal with the possibility of its absence. When the client does not set **PR_RENDERING_POSITION**, a message store can set it to -1 to indicate that the rendering position is not within the message text. Attachments with a rendering position of -1 can be displayed at any place within the message depending on the client. Many clients position these types of attachments at the top of the message.
  
The degree of accuracy for a **PR_RENDERING_POSITION** property depends on whether or not a message store saves both a message's **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) and **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) properties or only **PR_RTF_COMPRESSED**. If the client generates **PR_BODY** and the message store saves it along with the formatted text, the rendering positions will be accurate. However, if the message store must generate its own version of **PR_BODY** because it only saves **PR_RTF_COMPRESSED**, it is probable that the rendering positions will be somewhat inaccurate. This is because of the differences in the way that clients and message store providers generate the **PR_BODY** property. 
  
To calculate an accurate **PR_RENDERING_POSITION** value, an RTF-aware store uses a tag embedded in the formatted text. The utility function **RTFSync** can be called to perform this calculation and update an attachment's rendering position. Depending on the amount of state information available, the message store can pass either RTF_SYNC_BODY_CHANGED, RTF_SYNC_RTF_CHANGED, or both values to [RTFSync](rtfsync.md).
  

