---
title: "Outgoing Queue Tables"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 070377ca-ba9e-42ef-ac6b-ff7548b5ccf5
description: "An outgoing queue table contains information about outgoing messages for a message store. Providers implement outgoing queue tables for the MAPI spooler to use."
 
 
---

# Outgoing Queue Tables

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
An outgoing queue table contains information about all the outgoing messages for a message store. Message store providers implement outgoing queue tables for the MAPI spooler to use. Stores that do not support the sending or receiving of messages need not implement this table. 
  
To access an outgoing queue table, the MAPI spooler calls the [IMsgStore::GetOutgoingQueue](imsgstore-getoutgoingqueue.md) method. 
  
There is a requirement that messages be preprocessed and submitted to the transport provider in the same order as they were sent by the client application. The MAPI spooler is designed to accept messages from the message store in ascending order of submission time. Because of this requirement, there can be some delay before some messages appear in the outgoing queue table. 
  
Message stores should either allow sorting on the outgoing queue table so that the MAPI spooler can sort the messages by submission time, or the default sort order should be by ascending submission time. 
  
The outgoing queue table must send notifications when the contents of the queue changes.
  
The following properties make up the required column set in outgoing queue tables:
  
|Property |... |
|:-----|:-----|
|**PR_CLIENT_SUBMIT_TIME** ([PidTagClientSubmitTime](pidtagclientsubmittime-canonical-property.md))  <br/> |**PR_DISPLAY_BCC** ([PidTagDisplayBcc](pidtagdisplaybcc-canonical-property.md))  <br/> |
|**PR_DISPLAY_CC** ([PidTagDisplayCc](pidtagdisplaycc-canonical-property.md))  <br/> |**PR_DISPLAY_TO** ([PidTagDisplayTo](pidtagdisplayto-canonical-property.md))  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |**PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md))  <br/> |
|**PR_MESSAGE_SIZE** ([PidTagMessageSize](pidtagmessagesize-canonical-property.md))  <br/> |**PR_PRIORITY** ([PidTagPriority](pidtagpriority-canonical-property.md))  <br/> |
|**PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md))  <br/> |**PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md))  <br/> |
|**PR_SUBMIT_FLAGS** ([PidTagSubmitFlags](pidtagsubmitflags-canonical-property.md))  <br/> | <br/> |
   
For more information about how the outgoing queue table is used, see [Sending Messages by Using Message Store Providers](sending-messages-by-using-message-store-providers.md).
  
## See also



[MAPI Tables](mapi-tables.md)

