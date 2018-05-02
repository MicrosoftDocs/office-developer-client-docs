---
title: "Sending Messages by Using MAPI"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3edfbfff-ea15-4926-bf0f-47137251d921
description: "Last modified: July 23, 2011"
 
 
---

# Sending Messages by Using MAPI

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Client applications call the [IMessage::SubmitMessage](imessage-submitmessage.md) method to send a message. **SubmitMessage** calls [IMAPIProp::SaveChanges](imapiprop-savechanges.md) to save the message before transferring control to either the MAPI spooler or directly to a transport provider. 
  
The MAPI spooler receives the message if any of the following occur:
  
- The message store provider and transport provider are not tightly coupled.
    
- The message requires preprocessing.
    
- The tightly coupled message store and transport cannot handle all of the recipients to whom the message is addressed.
    
A tightly coupled message store must take into account a message's status before it presents it to the MAPI spooler to be downloaded to a transport provider. There are situations where a message may appear to require the MAPI spooler, but the MAPI spooler should really not be involved.
  
For example, consider the situation where a user submits a message from the Inbox. The client is using a tightly coupled store and transport. If the tightly coupled message store uses the message's location as the sole criteria for deciding about whether or not to allow the MAPI spooler to handle the message, the MAPI spooler will always receive the message. To avoid this kind of problem, a tightly coupled message store must check the message status in addition to message location. Specifically, the transport provider should not request that the MAPI spooler download any message that is actively submitted.
  
The message transmission process involves the message store provider, one or more transport providers, and MAPI. The topics in this section provide detailed information about specific roles in the message transmission process.
  
## See also

#### Reference

[IMessage::SubmitMessage](imessage-submitmessage.md)
  
[IMAPIProp::SaveChanges](imapiprop-savechanges.md)

