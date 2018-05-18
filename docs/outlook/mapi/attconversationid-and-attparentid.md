---
title: "attConversationID and attParentID"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: bed36900-e44d-434b-a4f2-d10f2d6f70da
description: "Last modified: March 12, 2013"
 
 
---

# attConversationID and attParentID

 
  
**Applies to**: Outlook 
  
The Windows for Workgroups 3.1 Mail conversation key is a text string. The MAPI equivalent is a binary value. To provide backward compatibility, the TNEF implementation converts the binary data to text and adds a terminating null character.
  
> [!NOTE]
> The corresponding properties in MAPI to which these TNEF attributes are mapped, PR_CONVERSATION_KEY and PR_PARENT_KEY, have been deprecated in Microsoft Exchange Server: Use of **PR_CONVERSATION_KEY**, the [PidTagConversationKey Canonical Property](pidtagconversationkey-canonical-property.md), persists in Outlook only, for locating **IPM.MessageManager** messages. 
  
## Remarks

The **PR_CONVERSATION_KEY** property is the otherwise obsolete precursor of the **PR_CONVERSATION_INDEX**, [PidTagConversationIndex Canonical Property](pidtagconversationindex-canonical-property.md) and **PR_CONVERSATION_TOPIC**, [PidTagConversationTopic Canonical Property](pidtagconversationtopic-canonical-property.md), which should be used instead.
  
## See also



[IPM Subtree](ipm-subtree.md)
  
[MAPI Special Folders](mapi-special-folders.md)

