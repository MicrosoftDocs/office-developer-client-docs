---
title: "Providing Notifications for Message Store Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: c0e1cdba-ceb6-4a3f-8449-79d1a0ad1adf
description: "Last modified: July 23, 2011"
 
 
---

# Providing Notifications for Message Store Providers

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
While notifications are optional, they are a very important part of a good message store provider. Client applications and the MAPI spooler rely on notifications from the message store provider to get good performance when submitting outgoing messages or receiving incoming messages. Clients and the MAPI spooler can function without receiving notifications from the message store provider, but they will not be able to inform users of changes in the message store without them. Typically, this means that users will be unable to see that a new message has arrived until their client next opens the message store's receive folder.
  
Clients register for notifications by calling the [IMsgStore::Advise](imsgstore-advise.md) method. The client passes in an [IMAPIAdviseSink : IUnknown](imapiadvisesinkiunknown.md) interface, a bitmask that indicates what type of notifications the client is interested in receiving, and an **EntryID** that indicates which object in the message store the **Advise** request applies to. When relevant events occur in the object (for example, when a new message arrives in the receive folder in the message store), the message store provider or the object itself should call the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for all of the **IMAPIAdviseSink** objects that have registered for that event type. 
  
Even if your message store provider never notifies other MAPI components of changes in the message store, it should still implement **IMsgStore::Advise** to return MAPI_E_NO_SUPPORT. This informs other components not to expect notifications from the message store provider. 
  
## See also

#### Concepts

[Message Store Features](message-store-features.md)

