---
title: "Timing a Notification"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 6981a3b0-96eb-44a2-b051-1c5efc70e9e3
description: "Last modified: July 23, 2011"
 
 
---

# Timing a Notification

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Because event notification is an asynchronous process, you can be notified at any time, not necessarily immediately after the event has occurred.
  
 The timing of calls to your [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method varies depending on the service provider implementing the advise source. Service providers can notify your client either: 
  
- Simultaneously with the event.
    
- Directly after the event.
    
- At some later point following the event, possibly after an **Unadvise** call. 
    
Most service providers call **OnNotify** after the MAPI method responsible for the event has returned to its caller. For example, notifications on messages are sent either when changes to the message are saved, after the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) call, or when the message is released, after the **IUnknown::Release** call. Until the notification is sent, no changes are visible in the message store. 
  
You can receive notifications from an advise source after you have called **Unadvise** to cancel a registration. Be sure to release your advise sink only after its reference count has fallen to zero, not following a successful **Unadvise** call. Do not assume that because you have called **Unadvise** that the advise sink is no longer necessary. 
  

