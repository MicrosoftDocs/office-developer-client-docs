---
title: "MAPI View Folders"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a1936ec2-bf8a-4242-a41d-64d26b813bd0
description: "Last modified: July 23, 2011"
 
 
---

# MAPI View Folders

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
View folders are root folders that contain associated information to define alternative display layouts for the contents of interpersonal message (IPM) folders. View folders reside under the root for the message store and, therefore, are not visible in the typical client application. Not every message store includes view folders; only message stores that are configured to work as the default message store for the session must include them.  
  
MAPI supports two view folders:
  
- Common — The common view folder contains views that are standard for the message store and can be used by any user of a client that accesses the message store. The entry identifier for the common view folder is stored in the store's **PR_COMMON_VIEWS_ENTRYID** ( [PidTagCommonViewsEntryId](pidtagcommonviewsentryid-canonical-property.md)) property.
    
- Personal — The personal view folder contains views that are defined by a particular user. MAPI defines the **PR_VIEWS_ENTRYID** ( [PidTagViewsEntryId](pidtagviewsentryid-canonical-property.md)) property for holding the entry identifier of the personal view folder. Using personal views, for example, one user could look at a group of messages sorted by sender, listing only the message subject and receipt date; another user could look at the same group sorted by date, listing the subject, sender, and message size.
    
## See also

#### Concepts

[MAPI Folders](mapi-folders.md)

