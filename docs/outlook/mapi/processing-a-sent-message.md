---
title: "Processing a Sent Message"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 55b3e692-753d-45e9-a40d-22adc81b75da
description: "Last modified: March 09, 2015"
 
 
---

# Processing a Sent Message

  
  
**Applies to**: Outlook 
  
Outgoing messages, after they have been sent, can be left in the Outbox folder, moved to a folder designated to hold sent messages, or deleted. The type of processing depends on whether or not you have set the message store properties:
  
- **PR_DELETE_AFTER_SUBMIT** ( [PidTagDeleteAfterSubmit](pidtagdeleteaftersubmit-canonical-property.md)) 
    
- **PR_SENTMAIL_ENTRYID** ( [PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md)) 
    
 **PR_DELETE_AFTER_SUBMIT** is a Boolean property, set to TRUE if messages should be deleted after they are sent, and FALSE otherwise. **PR_SENTMAIL_ENTRYID** is the entry identifier of a folder. When this property is set, you should move sent messages to the folder represented by this entry identifier. The saved messages typically have the identity of the last message store or transport provider to send them. 
  
Either one or the other, or neither of these properties should be set, but not both. However, if you set **PR_SENTMAIL_ENTRYID**, it must contain a valid entry identifier. 
  
The following table describes how these properties affect what you do with sent messages.
  
|||
|:-----|:-----|
|If neither property is set:  <br/> |Leave the message in the folder from which it was sent (typically the Outbox).  <br/> |
|If **PR_SENTMAIL_ENTRYID** is set:  <br/> |Move the message to the indicated folder.  <br/> |
|If **PR_DELETE_AFTER_SUBMIT** is set:  <br/> |Delete the message.  <br/> |
   

