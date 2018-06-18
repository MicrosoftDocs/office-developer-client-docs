---
title: "Canceling a Notification"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: decd5d7d-1f47-47c2-b9c4-be0e652c99dd
description: "Last modified: July 23, 2011"
 
 
---

# Canceling a Notification

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
To cancel a notification, clients call an advise source's **Unadvise** method. Calling **Unadvise** is important because it causes the service provider to release its reference to your advise sink. As long as a service provider maintains a reference to an advise sink, the advise sink can continue to receive [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) calls. In fact, because of the asynchronous nature of event notification, clients can be notified even after a successful **Unadvise** call. Clients must be able to handle the receipt of notifications at any time. 
  
Because service provider implementations differ, clients that fail to call **Unadvise** to cancel a notification cannot assume anything about when a provider will release its reference to their advise sink. Some service providers release their references to advise sinks when they release their advise sources. Some service providers do not. As long as a service provider maintains a reference to an advise sink, that advise sink can continue to receive notifications. 
  

