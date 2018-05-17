---
title: "Sending Messages by Using Message Store Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 7632d784-00d8-48fd-a73b-73778efbef7f
description: "Last modified: July 23, 2011"
 
 
---

# Sending Messages by Using Message Store Providers

  
  
**Applies to**: Outlook 
  
Message store providers are not required to support outgoing message submissions (that is, the ability for client applications to use the message store provider to send messages). Client applications need to use a message store while sending messages, because the message's data must be stored somewhere between the time that the user is finished composing it and the time that the MAPI spooler gives the message to a transport provider for submission to the underlying messaging system. If your message store provider does not support outgoing message submissions, it cannot be used as the default message store.
  
To support sending messages, your message store provider must do the following:
  
- Implement an outgoing message queue.
    
- Support the [IMessage::SubmitMessage](imessage-submitmessage.md) method on message objects created in the message store. 
    
- Support the **IMsgStore** methods that are specific to the MAPI spooler: [IMsgStore::FinishedMsg](imsgstore-finishedmsg.md), [IMsgStore::GetOutgoingQueue](imsgstore-getoutgoingqueue.md), [IMsgStore::NotifyNewMail](imsgstore-notifynewmail.md), and [IMsgStore::SetLockState](imsgstore-setlockstate.md).
    
The **SetLockState** method is important for proper interoperation between the MAPI spooler and clients. When the MAPI spooler calls **SetLockState** on an outgoing message, the message store provider must not let clients open the message. If a client does try to open a message that is locked by the MAPI spooler, the message store provider should return MAPI_E_NO_ACCESS. The locked state of a message does not have to be persistent in case the store is shut down while the message is locked by the MAPI spooler. 
  
Regardless of whether the MAPI spooler has locked an outgoing message, the message store provider should not allow a message in the outgoing message queue to be opened for writing. If a client calls the [IMSgStore::OpenEntry](imsgstore-openentry.md) method on an outgoing message with the MAPI_MODIFY flag, the call should fail and return MAPI_E_SUBMITTED. If a client application calls **OpenEntry** on an outgoing message with the MAPI_BEST_ACCESS flag, the message store provider should allow read-only access to the message. 
  
When a message is to be handled by the MAPI spooler, the message store provider sets the message's **PR_SUBMIT_FLAGS** ( [PidTagSubmitFlags](pidtagsubmitflags-canonical-property.md)) property to SUBMITFLAG_LOCKED. The SUBMITFLAG_LOCKED value indicates that the MAPI spooler has locked the message for its exclusive use. The other value for **PR_SUBMIT_FLAGS**, SUBMITFLAG_PREPROCESS, is set when the message requires preprocessing by one or more preprocessor functions registered by a transport provider.
  
The following procedures describe how the message store, transport, and MAPI spooler interact to send a message from a client to one or more recipients. 
  
The client application calls the [IMessage::SubmitMessage](imessage-submitmessage.md) method. In **SubmitMessage**, the message store provider does the following:
  
1. Calls [IMAPISupport::PrepareSubmit](imapisupport-preparesubmit.md). If MAPI returns an error, the message store provider returns that error to the client.
    
2. Sets the MSGFLAG_SUBMIT bit in the **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of the message.
    
3. Ensures that there is a column for the **PR_RESPONSIBILITY** ( [PidTagResponsibility](pidtagresponsibility-canonical-property.md)) property in the recipient table and sets it to FALSE to indicate that no transport has yet assumed responsibility for transmitting the message.
    
4. Sets the date and time of origination in the **PR_CLIENT_SUBMIT_TIME** ( [PidTagClientSubmitTime](pidtagclientsubmittime-canonical-property.md)) property.
    
5. Calls [IMAPISupport::ExpandRecips](imapisupport-expandrecips.md) to do the following: 
    
1. Expand all personal distribution lists and custom recipients and replace all changed display names with their original names.
    
2. Remove duplicate names.
    
3. Check for any required preprocessing and, if preprocessing is required, set the NEEDS_PREPROCESSING flag and the **PR_PREPROCESS** ( [PidTagPreprocess](pidtagpreprocess-canonical-property.md)) property, which is reserved for MAPI. 
    
4. Set the NEEDS_SPOOLER flag if the message store is tightly coupled with a transport and it cannot handle all of the recipients. 
    
6. Performs the following tasks if the NEEDS_PREPROCESSING message flag is set:
    
1. Puts the message in the outgoing queue with the SUBMITFLAG_PREPROCESS bit set in the **PR_SUBMIT_FLAGS** property. 
    
2. Notifies the MAPI spooler that the queue has changed.
    
3. Returns control to the client, and message flow continues in the MAPI spooler. The MAPI spooler performs the following tasks: 
    
1. Locks the message by calling [IMsgStore::SetLockState](imsgstore-setlockstate.md).
    
2. Performs the needed preprocessing by calling all of the preprocessing functions in the order of registration. Transport providers call [IMAPISupport::RegisterPreprocessor](imapisupport-registerpreprocessor.md) to register preprocessing functions. 
    
3. Calls [IMessage::SubmitMessage](imessage-submitmessage.md) on the open message to indicate to the message store that preprocessing is complete. 
    
If there was no preprocessing, or there was preprocessing and the MAPI spooler called **SubmitMessage**, the message store provider does the following in the client process: 
  
- Performs the following tasks if the message store is tightly coupled to a transport and the NEEDS_SPOOLER flag was returned from [IMAPISupport::ExpandRecips](imapisupport-expandrecips.md):
    
  - Handles any recipients that it can handle.
    
  - Sets the **PR_RESPONSIBILITY** property to TRUE for any recipients that it handles. 
    
  - Performs the following tasks if all recipients are known to this tightly coupled store and transport: 
    
  - Calls [IMAPISupport::CompleteMsg](imapisupport-completemsg.md) if the message was preprocessed or the message store provider wants the MAPI spooler to complete message processing. Message flow continues with the MAPI spooler. 
    
  - Performs the following tasks if the message was not preprocessed or the message store provider does not want the MAPI spooler to complete message processing:
    
1. Copies the message to the folder identified by the entry identifier in the **PR_SENTMAIL_ENTRYID** ( [PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md)) property, if set.
    
2. Deletes the message if the **PR_DELETE_AFTER_SUBMIT** ( [PidTagDeleteAfterSubmit](pidtagdeleteaftersubmit-canonical-property.md)) property has been set to TRUE.
    
3. Unlocks the message if it is locked.
    
4. Returns to the client. Message flow is complete.
    
  - Performs the following tasks if the message was preprocessed or the provider wants the MAPI spooler to complete message processing:
    
1. Calls [IMAPISupport::CompleteMsg](imapisupport-completemsg.md). 
    
2. Continues message flow with the MAPI spooler. For more information, see [Sending Messages: MAPI Spooler Tasks](sending-messages-mapi-spooler-tasks.md).
    
  - Performs the following tasks if the message was not preprocessed or the provider does not want the spooler to complete message processing:
    
1. Copies the message to the folder identified by the entry identifier in the **PR_SENTMAIL_ENTRYID** property, if set. 
    
2. Deletes the message if the **PR_DELETE_AFTER_SUBMIT** property has been set to TRUE. 
    
3. Unlocks the message if it is locked. 
    
4. Returns to the caller. Message flow is complete.
    
- Performs the following tasks if the message store is not tightly coupled to a transport, not all of the recipients were known to the message store, or the NEEDS_SPOOLER flag is set:
    
1. Puts the message in the outgoing queue without setting the SUBMITFLAG_PREPROCESS bit in the **PR_SUBMIT_FLAGS** property. 
    
2. Notifies the MAPI spooler that the outgoing queue has changed by generating a table notification. 
    
3. Returns to the client, and message flow continues with a set of tasks performed by the MAPI spooler.
    
## See also

#### Concepts

[Message Store Features](message-store-features.md)

