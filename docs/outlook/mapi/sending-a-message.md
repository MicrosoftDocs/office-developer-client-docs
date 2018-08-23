---
title: "Sending a Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4fa47824-b4ef-41e1-9096-c1b1cdacd7ac
description: "Last modified: July 23, 2011"
 
 
---

# Sending a Message

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When you are ready to send a message, call its [IMessage::SubmitMessage](imessage-submitmessage.md) method. **SubmitMessage** places the message in the outgoing queue and sets the MSGFLAG_SUBMIT flag in the message's **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property.
  
The message store provider, if tightly coupled to a transport provider, gives the message directly to the transport which delivers it to the messaging system. If not tightly coupled, the message store provider informs the MAPI spooler that the outgoing queue has changed and the MAPI spooler transfers the message to an appropriate transport provider.
  
If you allow users to cancel a send operation, call [IMsgStore::AbortSubmit](imsgstore-abortsubmit.md) to implement this feature. **AbortSubmit** removes the message from the outgoing queue. Users can be allowed to stop a send from happening until the message is given to the underlying messaging system. 
  
If **SubmitMessage** returns MAPI_E_CORRUPT_DATA, assume that the data being sent is now lost. Before attempting to send a second time, re-write the message by calling [IMAPIProp::SetProps](imapiprop-setprops.md) and [IMAPIProp::SaveChanges](imapiprop-savechanges.md). Display an error to the user if these **IMAPIProp** calls fail or if **SubmitMessage** fails a second time. 
  
After a successful call to **SubmitMessage**, free any memory that was allocated for the recipient list and release the message and its attachments. Once a message has been sent, MAPI does not permit any further operations on the pointers for these objects. The one exception is calling **IUnknown::Release**. No other calls are allowed because many message store providers invalidate entry identifiers for messages that have been sent.
  

