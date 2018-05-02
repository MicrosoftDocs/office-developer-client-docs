---
title: "Special Folders in Message Stores"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9462070e-1472-4e12-ba4e-e4ac60022892
description: "Last modified: July 23, 2011"
 
 
---

# Special Folders in Message Stores

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Special folders such as the Inbox, Outbox, and search-results folder may be created in advance and protected by the message store provider. If the folders do not exist, MAPI will attempt to create them in the message store by calling the [HrValidateIPMSubtree](hrvalidateipmsubtree.md) function. For more information, see [MAPI Special Folders](mapi-special-folders.md).
  
## See also

#### Concepts

[Implementing Folders in Message Stores](implementing-folders-in-message-stores.md)

