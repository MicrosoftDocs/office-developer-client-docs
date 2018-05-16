---
title: "Supporting Formatted Text Gateway Responsibilities"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: de737118-5f3b-464f-b036-f4a3489d411a
description: "Last modified: July 23, 2011"
 
 
---

# Supporting Formatted Text: Gateway Responsibilities

  
  
**Applies to**: Outlook 
  
 **To handle Rich Text Format for outgoing messages, gateways**
  
1. Retrieve only a message's **PR_RTF_COMPRESSED** ( [PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property from the message store. The main advantage in retrieving only the **PR_RTF_COMPRESSED** property is that the message text does not need to be sent between machines if the gateway and the message store exist on different machines. 
    
2. Generate the message text from the formatted text either by calling the RTF library function **HrTextFromCompressedRTFStream** or, if the message is stored locally, **RTFSync**. The RTF_SYNC_RTF_CHANGED flag should be set in the call to **RTFSync**. For more information, see [RTFSync](rtfsync.md).
    
3. Make any irreversible modifications to the message text, such as dropping unsupported characters. 
    
4. Ensure that both **PR_RTF_IN_SYNC** ( [PidTagRtfInSync](pidtagrtfinsync-canonical-property.md)) and all of the RTF auxilliary properties are either set or absent.
    
5. If any modifications were made, call **RTFSync** with both the RTF_SYNC_RTF_CHANGED and RTF_SYNC_BODY_CHANGED flags set. **RTFSync** will recalculate the RTF auxilliary properties from the modified text. 
    
6. Make any reversable modifications to the message text, such as inserting attachment placeholders and performing nondestructive code page conversions.
    
7. Send the message.
    
 **To handle Rich Text Format for incoming messages, gateways**
  
1. Reverse any message text modifications that were made directly before the message was sent. 
    
2. Call **RTFSync** if the message contains both the **PR_RTF_COMPRESSED** and **PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md)) properties. 
    
3. Update the message in the message store with the **PR_RTF_COMPRESSED** property if the message contains it; update with the **PR_BODY** property only if **PR_RTF_COMPRESSED** is absent. 
    
4. Discard **PR_BODY** if the message contains both this property and **PR_RTF_COMPRESSED**.
    
Gateways call **RTFSync** to avoid transmitting both the message text and formatted text if the message store is on a different machine. If the gateway is local, it can set both properties and allow the message store to perform the synchronization. 
  

