---
title: "IMAPISupportNotify"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.Notify
api_type:
- COM
ms.assetid: c16c668e-2c8b-4759-bbca-d0c5662b62e9
description: "Last modified: July 23, 2011"
---

# IMAPISupport::Notify

  
  
**Applies to**: Outlook 
  
Sends a notification of a specified event to an advise source that originally registered for the notification through the [IMAPISupport::Subscribe](imapisupport-subscribe.md) method. 
  
```
HRESULT Notify(
LPNOTIFKEY lpKey,
ULONG cNotification,
LPNOTIFICATION lpNotifications,
ULONG FAR * lpulFlags
);
```

## Parameters

 _lpKey_
  
> [in] A pointer to the notification key for the advise source object. The  _lpKey_ parameter cannot be NULL. 
    
 _cNotification_
  
> [in] The count of notification structures pointed to by the  _lpNotifications_ parameter. 
    
 _lpNotifications_
  
> [in] A pointer to an array of [NOTIFICATION](notification.md) structures that describe pending notifications. 
    
 _lpulFlags_
  
> [in, out] A bitmask of flags that controls the notification process. On input, the following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the notification structures pointed to by  _lpNotifications_ are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
    On output, MAPI can set the following flag:
    
NOTIFY_CANCELED 
  
> A callback function canceled a synchronous notification.
    
## Return value

S_OK 
  
> The notifications were successfully generated.
    
## Remarks

The **IMAPISupport::Notify** method is implemented for all service provider support objects. Service providers call **Notify** to request that MAPI generate a notification for an advise sink that has previously registered for the notification through the **IMAPISupport::Subscribe** method. 
  
 **Notify** copies the structures pointed to by the  _lpNotifications_ parameter into memory and calls the appropriate advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method. When **OnNotify** is finished with the notification, it releases the memory involved. The caller does not need to allocate memory; MAPI performs all necessary memory allocation. 
  
## Notes to Callers

The notification key passed in the  _lpKey_ parameter should be identical to the key passed in  _lpKey_ to the **IMAPISupport::Subscribe** method. Many providers use the entry identifier of the advise source as the key, but other data, such as a file path, can be used. MAPI uses this key to find all the registrations for notifications on the identified advise source. 
  
Be sure that you set the **lpEntryID** member of the notification structure to a long-term entry identifier. 
  
If you set the NOTIFY_SYNC flag on the **Subscribe** call for any of the pending notifications, **Notify** calls the **IMAPIAdviseSink::OnNotify** method callback functions before returning. An advise sink can be created manually or by calling [HrAllocAdviseSink](hrallocadvisesink.md). The **HrAllocAdviseSink** function allows its caller to specify a callback function that **Notify** calls as part of the notification. The callback function conforms to the [NOTIFCALLBACK](notifcallback.md) prototype. Callback functions implemented by clients always return S_OK; callback functions implemented by service providers can return CALLBACK_DISCONTINUE. 
  
If a callback function returns CALLBACK_DISCONTINUE, MAPI stops sending notifications and returns NOTIFY_CANCELED in the **Notify** method's  _lpulFlags_ parameter. You can assume that the process is inactive and stop generating notifications for that process. If **Notify** returns 0 in  _lpulFlags_, the process is still active and you should continue to send notifications, as appropriate.
  
When you use synchronous notifications, be careful to avoid deadlock situations.
  
For more information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). 
  
## See also

#### Reference

[IMAPISupport::Subscribe](imapisupport-subscribe.md)
  
[IMAPISupport::Unsubscribe](imapisupport-unsubscribe.md)
  
[NOTIFCALLBACK](notifcallback.md)
  
[NOTIFICATION](notification.md)
  
[NOTIFKEY](notifkey.md)
  
[PidTagRecordKey Canonical Property](pidtagrecordkey-canonical-property.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

