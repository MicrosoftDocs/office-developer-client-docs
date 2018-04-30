---
title: "Long-Term Entry Identifiers"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: a514275e-40c2-48db-8072-1dfc392a7ac6
description: "Last modified: July 23, 2011"
---

# Long-Term Entry Identifiers

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A long-term entry identifier is assigned by a service provider to an object when an object requires an identifier with a prolonged lifespan. Long-term entry identifiers are always valid for weeks or months and can be valid on other workstations, depending on the provider. The long-term identifiers created by address book providers for custom recipients are universally valid. 
  
Long-term entry identifiers are assigned to message stores, folders, messages, address book containers, messaging users, and distribution lists. When client applications call the [IMAPIProp::GetProps](imapiprop-getprops.md) method of these objects, it is always a long-term entry identifier that is returned. 
  
Long-term entry identifiers must be unique across all message stores in the active profile; therefore, when a message or folder is copied from one message store to another, it must be assigned a new entry identifier. When a message store object is moved, the message store provider that implements the move determines whether the original entry identifier will remain valid. Some service providers assign new entry identifiers to moved objects; others do not. If there is a change, the new entry identifier will be included in the information passed to clients when they are notified of the move. 
  
Typically, message store providers implement the following behavior when they move folders:
  
- When a folder is moved from one message store to another store of a different type, the entry identifier is guaranteed to change.
    
- When a folder is moved from one message store to another store of the same type, the entry identifier almost always changes.
    
- When a folder is moved to another location within the same message store, the entry identifier might or might not change, depending on the message store provider.
    
Renaming a folder without changing its parent folder usually does not cause the entry identifier to change. 
  
## See also

#### Concepts

[MAPI Entry Identifiers](mapi-entry-identifiers.md)

