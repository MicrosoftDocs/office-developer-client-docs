---
title: "MAPI Messages"
description: Provides a detailed overview of MAPI messages and transmission from one client application to another through the MAPI spooler and service providers.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 417c113f-bd98-4515-85d1-09db7fc3a227
---

# MAPI Messages

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Messages are MAPI objects that are transmitted from one client application to another through the MAPI spooler and service providers by way of a messaging system. Nearly every component in MAPI works with messages. Clients let users create, save, send, and delete messages in addition to copy and move them from one folder to another. Message store providers are responsible for message management and for delivering messages to the MAPI spooler or a transport provider. The MAPI spooler moves messages to an appropriate transport provider, whereas transport providers handle the delivery and receipt of messages to and from a messaging system and set recipient and message option properties. Address book providers work indirectly with messages, supporting properties that describe message recipients.
  
Messages are stored in folders throughout a message store, typically folders created in the interpersonal message (IPM) root folder. Messages are usually stored at the same level as the standard IPM Inbox, Sent Items, Deleted Items, and Outbox folders, or at lower levels in the hierarchy. However, messages can also be stored outside the IPM subtree.
  
Messages created in the standard IPM subtree have standard contents (that is, contents that are visible to the user of a client application). Notes and reports are examples of messages that have standard contents. Messages can also be created with associated contents, or contents that are not visible in the typical client. Folders support two different contents tables to hold the different types of messages: a standard contents table for standard messages, and an associated contents table for associated messages. Because MAPI does not set standards for the content of associated messages, they can contain arbitrary information. 
  
A message can have additional data — in the form of a file, another message, or an OLE object — associated with it. This additional data, which is called an attachment, appears either as an icon or, for an RTF message, as a metafile in the message text. A message can have zero, one, or many attachments. Attachments are always transmitted with the message.
  
A message that is transmitted has one or more recipients (addresses that are associated with a particular messaging system). Some recipients are entries in a container that belongs to an address book provider in the current profile; other recipients are created only to transmit the message. Because recipients and attachments must be accessed through the message with which they are associated, a message's recipients and attachments are known as its subobjects. 
  
Message store providers support messages, attachments, and recipients through methods in three interfaces: 
  
|**Interface**|**Description**|
|:-----|:-----|
|[IMessage](imessageimapiprop.md) <br/> |Manages attachments and recipients, sends messages, sets read status. |
|[IMAPIFolder](imapifolderimapicontainer.md) <br/> |Creates, copies, and moves messages and subfolders and manages message status. |
|[IAttach](iattachimapiprop.md) <br/> |Manages attachment properties. |
   
## See also



[MAPI Application Development](mapi-application-development.md)

