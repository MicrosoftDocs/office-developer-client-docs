---
title: "Handling notifications"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 451b71da-a888-4d8f-9814-12f9f846de05
---

# Handling notifications

**Applies to**: Outlook 2013 | Outlook 2016
  
Notifications enable one object to inform another object that it has undergone a change. The type of change is referred to as an event. MAPI defines several events for which notifications are generated.
  
Clients typically register for one or more events with one or more objects. These objects are referred to as advise sources. Objects that can act as advise sources include the session object, under MAPI's control, or an object created by a service provider, such as a message. The informed object, referred to as the advise sink, contains either an implementation of the [IMAPIAdviseSink : IUnknown](imapiadvisesinkiunknown.md) interface or the [IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md) interface and is within a client application.
  
Advise source objects implement an **Advise** method, which is called by clients to register for notifications, and an **Unadvise** method, which is called to cancel a registration. One of the parameters to **Advise** is a pointer to an implementation of **IMAPIAdviseSink** orIMAPIViewAdviseSink**. The advise source caches this pointer so that it can call [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) or one of the methods in**IMAPIViewAdviseSink** when a change occurs.
  
Because receiving notifications enables users to view the most up-to-date information, it is recommended that all clients register for and handle notifications. However, it is optional.
  
## In this section

- [Registering for a Notification](registering-for-a-notification.md): Describes how to register a client for notifications as a part of its initialization process.

- [Canceling a Notification](canceling-a-notification.md): Describes how to cancel a subscription to a notification.

- [Handling Message Store Notification](handling-message-store-notification.md): Describes how to register for message store notifications.

- [Handing Address Book Notification](handing-address-book-notification.md): Describes how to register for and handle address book notifications.

- [Handling Table Notification](handling-table-notification.md): Describes how to register for notifications from the hierarchy table.

- [Implementing an Advise Sink Object](implementing-an-advise-sink-object.md): Describes how to implement an advise sink object.

- [Timing a Notification](timing-a-notification.md): Describes the timing of client notification by service providers.

- [Ensuring a Thread-Safe Notification](ensuring-a-thread-safe-notification.md): Describes how to ensure thread-safe notification with MAPI.

- [Forcing a Notification](forcing-a-notification.md): Describes how to force a notification in MAPI.
