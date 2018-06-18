---
title: "Short-term entry identifiers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 948e007a-ad68-4abd-9720-204c6584beb5
description: "Last modified: July 23, 2011"
---

# Short-term entry identifiers

**Applies to**: Outlook 2013 | Outlook 2016 
  
A short-term entry identifier is assigned by a service provider to an object when the identifier must be constructed quickly and does not need to last over time or distance. The uniqueness of a short-term entry identifier is guaranteed only over the life of the current session on the current workstation. Typically, a short-term entry identifier is valid only until the object that it represents is released. 
  
Short-term entry identifiers are assigned to rows in tables and to entries in dialog boxes, where it is necessary to provide data quickly for browsing. For example, message store providers assign short-term entry identifiers to rows of messages in a contents table and to recipients in a recipients table. 

Clients can use these short-term entry identifiers to open the objects represented by the table rows. However, unlike long-term entry identifiers that can be used with any of the **OpenEntry** methods, short-term entry identifiers should be used with the container's **OpenEntry** method. 
  
## Implementing short-term entry identifiers

The most common ways to implement short-term entry identifiers include the following:
  
- Making the short-term entry identifiers the same as the long-term identifiers, leaving all of the flags unset. 
    
- Making the short-term entry identifiers different from the long-term identifiers, setting all of the flags. 
    
Clients can identify a short-term entry identifier of the second type by examining its **abFlags** member as follows: 
  
```cpp
abFlags[0] = 0xFF;
 
```

Some service providers clear one or more flags to create short-term entry identifiers that have greater validity. For example, the following **abFlags** members represent short-term entry identifiers that can be used for multiple days or for multiple sessions: 
  
```cpp
abFlags[0] = 0xFF & ~MAPI_NOW;
abFlags[0] = 0xFF & ~MAPI_THISSESSION;
 
```

Clients quickly acquire, use, and discard short-term entry identifiers. For the most part, they can be used in the same manner as long-term entry identifiers. They can be retrieved from a table, passed to the **OpenEntry** method, and compared with the **CompareEntryIDs** method. The one exception is that they are never returned from the [IMAPIProp::GetProps](imapiprop-getprops.md) method. The properties returned from **GetProps** are always long-term entry identifiers. 
  
## See also

- [MAPI Entry Identifiers](mapi-entry-identifiers.md)

