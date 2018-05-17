---
title: "MAPI Entry Identifiers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 84c37696-da7a-42e0-b8c0-29658a6c9a48
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Entry Identifiers

  
  
**Applies to**: Outlook 
  
Entry identifiers are pieces of binary data stored in an [ENTRYID](entryid.md) structure that are used to uniquely identify and open a MAPI object. Most MAPI objects have entry identifiers. Entry identifiers for objects are analogous to file names for files. However, they are not transmittable and cannot be used on systems other than the system they originated on. 
  
## Entry Identifiers

Message store providers assign entry identifiers to message stores, folders, and messages; address book providers assign them to address book containers, distribution lists, and messaging users. Entry identifiers are also used to open an object represented by a row in a table, such as a status object in the status table. Objects store their entry identifiers in their **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property. 
  
Whereas service providers create, assign, and examine entry identifiers, client applications use them only as tools for opening objects. To clients, entry identifiers are opaque pieces of binary data and have nothing to do with the underlying messaging system. 
  
Clients call an object's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve its **PR_ENTRYID** property or a table's [IMAPITable::QueryColumns](imapitable-querycolumns.md) method to retrieve the column that holds the **PR_ENTRYID** property. 
  
Entry identifiers are passed as parameters to the **OpenEntry** and **CompareEntryIDs** methods. Several MAPI objects implement the **OpenEntry** and **CompareEntryIDs** methods. With **OpenEntry**, clients can open an object. With **CompareEntryIDs**, clients can compare two entry identifiers to determine whether they refer to the same object. Because entry identifiers are not necessarily binary comparable, clients must compare them by the **CompareEntryIDs** method. 
  
Clients should always pass naturally aligned entry identifiers in their calls to service providers, because although service providers should handle entry identifiers that are arbitrarily aligned, this is not always the case. A naturally aligned memory address enables the computer to access any data type it supports at that address without generating an alignment fault. The natural alignment factor is typically the same alignment factor used by the system memory allocator and is usually 8 bytes.
  
Entry identifiers come in two types: short-term and long-term. Short-term entry identifiers are faster to construct, but their uniqueness is guaranteed only over the life of the current session on the current workstation. Long-term entry identifiers have a more prolonged lifespan. Short-term entry identifiers are used primarily for rows in tables and entries in dialog boxes, whereas long-term entry identifiers are used for many objects such as messages, folders, and distribution lists.
  
## See also

#### Concepts

[MAPI Application Development](mapi-application-development.md)

