---
title: "IMAPISupportSubscribe"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.Subscribe
api_type:
- COM
ms.assetid: e6baaff1-446e-431a-a09b-9b529153382b
description: "Last modified: July 23, 2011"
---

# IMAPISupport::Subscribe

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Registers an advise sink to receive notifications through MAPI.
  
```
HRESULT Subscribe(
LPNOTIFKEY lpKey,
ULONG ulEventMask,
ULONG ulFlags,
LPMAPIADVISESINK lpAdviseSink,
ULONG FAR * lpulConnection
);
```

## Parameters

 _lpKey_
  
> [in] A pointer to a notification key that represents the advise source object. The  _lpKey_ parameter cannot be NULL. 
    
 _ulEventMask_
  
> [in] A mask of values that indicate the types of notification events that the caller is interested in and should be included in the registration. The following values are valid:
    
 _fnevCriticalError_
  
> Registers for notifications about severe errors, such as insufficient memory.
    
 _fnevExtended_
  
> Registers for notifications about events specific to the particular address book or message store provider.
    
 _fnevNewMail_
  
> Registers for notifications about the arrival of new messages. 
    
 _fnevObjectCreated_
  
> Registers for notifications about the creation of a new object.
    
 _fnevObjectCopied_
  
> Registers for notifications about an object being copied.
    
 _fnevObjectDeleted_
  
> Registers for notifications about an object being deleted.
    
 _fnevObjectModified_
  
> Registers for notifications about an object being modified.
    
 _fnevObjectMoved_
  
> Registers for notifications about an object being moved.
    
 _fnevSearchComplete_
  
> Registers for notifications about the completion of a search operation.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how notification occurs. The following flag can be set:
    
NOTIFY_SYNC 
  
> When the caller calls the [IMAPISupport::Notify](imapisupport-notify.md) method to generate notifications for this advise sink, **Notify** should make all necessary calls to advise sinks before returning. If this flag is not set, notification is asynchronous and callbacks are queued to the processes that have subscribed and started when those processes gain control of the CPU. 
    
 _lpAdviseSink_
  
> [in] A pointer to an advise sink object. 
    
 _lpulConnection_
  
> [out] A pointer to a nonzero connection number that represents the registration.
    
## Return value

S_OK 
  
> The notification registration was successful.
    
## Remarks

The **IMAPISupport::Subscribe** method is implemented for all service provider support objects. Service providers call **Subscribe** from one of their **Advise** methods to allow MAPI to manage the notifications. 
  
## Notes to Callers

To use the MAPI support methods for notification, create a key for the advise source the object about which notifications should be generated. The value of the key must be unique and should be easily regenerated each time the object changes. 
  
MAPI uses the notification key to search for any callback functions registered through the [HrAllocAdviseSink](hrallocadvisesink.md) function for the corresponding advise source. Pass this key to **IMAPISupport::Notify** whenever you need to generate a notification for the corresponding advise source. 
  
The NOTIFY_SYNC flag affects the operation of subsequent calls to **Notify**. When you set NOTIFY_SYNC, **Notify** does not return until it has finished sending all of the necessary notifications. When you do not set NOTIFY_SYNC, **Notify** operates asynchronously, possibly returning before all of the notifications have been sent. 
  
## See also

#### Reference

[HrAllocAdviseSink](hrallocadvisesink.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMAPISupport::Notify](imapisupport-notify.md)
  
[NOTIFICATION](notification.md)
  
[NOTIFKEY](notifkey.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

