---
title: "Supporting Event Notification"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a1e3e49c-8d1d-4f7e-ba5a-be441f0f10ae
description: "Last modified: July 23, 2011"
 
 
---

# Supporting Event Notification

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Because supporting event notification can be complicated, MAPI supplies three support object methods that implement the most difficult parts of the process. These methods work as a unit, and a provider must use all three or none of them.
  
The MAPI support methods use notification keys to manage the connections between the advise sinks and the objects that generate the notifications. A notification key is a [NOTIFKEY](notifkey.md) structure that contains binary data that identifies an object across processes. A notification key is typically copied from the long-term entry identifier of the advise source object. If the client has supplied an entry identifier in the call to **Advise**, you can use it for the notification key. If the  _lpEntryID_ parameter to **Advise** is NULL, use the entry identifier of the outermost possible container object, such as the message store. 
  
To use the support methods, call [IMAPISupport::Subscribe](imapisupport-subscribe.md) whenever a client calls your **Advise** method to register for a notification. Allocate a [NOTIFKEY](notifkey.md) structure and create a unique notification key for your advise source object. For example, a message store provider that is prompted to notify a client when a message is received into a particular folder creates a notification key for that folder. Pass a pointer to the **NOTIFKEY** structure in the call to **Subscribe** along with a pointer to the client's advise sink. **Subscribe** calls the advise sink's [IUnknown::AddRef](https://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx) method to increment its reference count and MAPI retains the pointer until the registration is canceled. 
  
You can pass the NOTIFY_SYNC flag to **Subscribe** to request that **Notify** behave synchronously and not return until it has made all calls to the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) methods of registered advise sinks. Set this flag only for your own internal use. Do not set it when you respond to a client **Advise** call. Event notification between clients and providers is always asynchronous. That is, MAPI guarantees that the call during which an event happens will return to the client before any of the **OnNotify** calls are made. 
  
If you set the NOTIFY_SYNC flag, do not make any changes to any of the advise sink objects, and do not pass a wrapper advise sink created by [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) to **Subscribe**. **HrThisThreadAdviseSink** creates a thread-safe version of an advise sink to be used with asynchronous notification only. 
  
If an advise sink registered for synchronous notification returns from **OnNotify** with the CALLBACK_DISCONTINUE flag set, [IMAPISupport::Notify](imapisupport-notify.md) sets the NOTIFY_CANCELED flag and returns without making any calls to **OnNotify**. 
  
Once **Subscribe** has returned, you will no longer have any need to hold onto your copy of the client's advise sink. Call its [IUnknown::Release](https://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method to release it. **Subscribe** returns a nonzero connection number that you should return to the client. The connection number represents the link between the advise source and the advise sink. It remains valid until the client makes a successful call to **Unadvise**. 
  
When the client is ready to cancel a registration, it calls your **Unadvise** method. Pass the connection number from the **Unadvise** call to [IMAPISupport::Unsubscribe](imapisupport-unsubscribe.md). **Unsubscribe** calls the advise sink's **IUnknown::Release** method. As with **Advise** and **Unadvise**, calls to **Subscribe** and **Unsubscribe** must be paired. You must make one call to **Unsubscribe** for every call that is made to **Subscribe**. However, you do not have to call **Subscribe** every time your **Advise** method is called. Conversely, you can call it for setting up internal notifications. 
  
When an event occurs, allocate one or more [NOTIFICATION](notification.md) structures of the type appropriate for the event and call [IMAPISupport::Notify](imapisupport-notify.md). **Notify** generates a notification for each registered advise sink. You should set all the unused members of the [NOTIFICATION](notification.md) structure to zero. This technique for initializing the **NOTIFICATION** structure can help clients create smaller, faster, and less error-prone **OnNotify** implementations. 
  
Note that a separate **NOTIFICATION** structure is necessary for each event, even for multiple events of the same type. For example, if three clients are registered for table notification on a particular table and five rows are added to the table, you must create five **OBJECT_NOTIFICATION** structures for your **Notify** call. A batch notification such as this results in better performance than calling **Notify** five times. For each **Notify** call, MAPI calls the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method of every registered advise sink. If there are no registered advise sinks, MAPI ignores the call. 
  
Service providers that send batched notifications must order them so that they can be interpreted from the first notification to the last. This ordering is especially necessary when a notification batch contains a series of events, such as TABLE_ROW_ADDED with one event that refers to a prior row that was added in another event in the same batch.
  
## See also



[MAPI Service Providers](mapi-service-providers.md)

