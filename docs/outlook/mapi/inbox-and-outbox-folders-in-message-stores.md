---
title: "Inbox and Outbox Folders in Message Stores"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 8e4ce129-137d-4618-80a6-88781a578d01
description: "Last modified: July 23, 2011"
 
 
---

# Inbox and Outbox Folders in Message Stores

  
  
**Applies to**: Outlook 
  
To be the default message store, a message store provider must implement Inbox and Outbox folders. They are typically stored in the IPM subtree of a message store. These folders are special in that they are designated as the folders that messages are delivered to and sent from, but no special functionality is required of them. Sending and receiving messages happens by way of defined call sequences between client applications, the MAPI spooler, and the message store provider. The Inbox and Outbox folders are simply folders that are used to hold messages during those call sequences. The important point is not that the folders are special, or even that they are named Inbox and Outbox; the important point is that the message store provider uses them as part of its support for sending and receiving messages.
  
To support receiving messages, the message store provider must implement the [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) and [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md) methods. For more information, see [Receiving Messages by Using Message Store Providers](receiving-messages-by-using-message-store-providers.md).
  
To support sending messages, the message store provider must support the [IMsgStore::GetOutgoingQueue](imsgstore-getoutgoingqueue.md) method, in addition to the other methods used by the MAPI spooler during the message sending process. A message store's outgoing queue does not have to correspond to an actual folder anywhere in the message store's folder tree. However, it is customary for a message store provider to show the contents of the outgoing message queue in the Outbox folder, if there is one. Doing so gives client applications a convenient way to indicate the status of messages that the user has sent, because an Outbox folder can be displayed along with all the other folders in a message store. For more information, see [Sending Messages by Using Message Store Providers](sending-messages-by-using-message-store-providers.md).
  
## See also

#### Concepts

[Implementing Folders in Message Stores](implementing-folders-in-message-stores.md)

