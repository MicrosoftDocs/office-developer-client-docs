---
title: "Message Content"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: ce643afe-e5b6-42f2-b3cf-4efb957c4f2e
description: "Last modified: July 23, 2011"
 
 
---

# Message Content

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
There are two possible encodings for the message content: one using MIME, the other using uuencode. MIME is the preferred encoding. In addition, MAPI defines a per-recipient property, **PR_SEND_RICH_INFO** ( [PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)), which governs whether or not TNEF information should be included in an outgoing message. So there are a total of four ways of encoding message content:
  
- MIME with TNEF
    
- MIME without TNEF
    
- uuencode with TNEF
    
- uuencode without TNEF
    
How to choose MIME or uuencode for outbound messages is not specified.
  
The following properties are excluded from TNEF: **PR_SENDER_\***, **PR_ATTACH_DATA_\***, **PR_BODY**. All other transmittable message properties are included in the TNEF stream.
  
The following suggestions are intended to provide a list of parameters that the implementation can decide how to support:
  
- Whether to encode using MIME or uuencode for outbound messages: boolean.
    
- Character set to use for outbound messages: string (copied directly to charset parameter) or enumeration (translated internally to charset string).
    

