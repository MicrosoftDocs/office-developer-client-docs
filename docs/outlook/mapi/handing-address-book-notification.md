---
title: "Handing Address Book Notification"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 0dc4bb48-c8a1-447f-9e38-1c234a358fca
description: "Last modified: July 23, 2011"
---

# Handing Address Book Notification

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Address book notifications allow a client to learn of events that occur to any address book entry or to a particular entry. You can register for these notifications either through the MAPI address book by calling [IAddrBook::Advise](iaddrbook-advise.md) or through an address book container's hierarchy or contents table by calling [IMAPITable::Advise](imapitable-advise.md). 
  
Specify the entry identifier of an address book container, distribution list, or messaging user if you are registering for notifications on a particular entry and NULL if registering for notifications on the entire address book. The entry identifier must represent a messaging user or distribution list in an address book container. **IAddrBook::Advise** examines this entry identifier to determine which address book provider is responsible for the corresponding object and forwards the call to the appropriate address book provider's [IABLogon::Advise](iablogon-advise.md) method. 
  
Clients can register for the following types of events on address book entries:
  
- Critical error
    
- Any of the object events (created, modified, deleted, moved, or copied)
    
- Table modified
    
Typically, registration occurs only on address book container contents and hierarchy tables. It is rare that clients register with the lower level messaging user and distribution list objects. This is because:
  
- Many address book providers do not support notifications on their messaging users and distribution lists.
    
- Table notifications are sufficient for tracking changes and reporting them to users.
    

