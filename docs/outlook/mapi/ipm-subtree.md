---
title: "IPM Subtree"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b5fc6084-722d-44e8-8637-f4160a4fb19b
description: "Last modified: July 23, 2011"
 
 
---

# IPM Subtree

  
  
**Applies to**: Outlook 
  
MAPI creates a tree of folders beneath the root folder of a message store for all clients that send messages to and receive messages from human, rather than computer, recipients. Messages exchanged between human recipients are known as interpersonal messages, and this tree is known as the interpersonal message, or IPM, subtree. 
  
An IPM subtree for a delivery store consists of at least the following folders:
  
- Inbox
    
- Outbox
    
- Sent Items
    
- Deleted Items
    
These are the default names and roles for each of these folders; a client can specify its own names if the default names are not appropriate. MAPI assigns default names and associations for these folders to keep messages from inadvertently disappearing if a client neglects to establish receiving folders for messages. 
  
In a Microsoft Office Outlook context, an IPM subtree consists of additional default folders for Calendar, Contacts, Tasks, Notes, and Journal.
  
The Inbox typically holds incoming messages, and the Outbox holds outgoing messages (that is, messages waiting to be sent). The Sent Items folder holds a copy of each sent message if the client has set the **PR_SENTMAIL_ENTRYID** ([PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md)) property to the entry identifier of this folder. The Deleted Items folder contains messages marked for removal. 
  
## See also



[MAPI Folders](mapi-folders.md)

