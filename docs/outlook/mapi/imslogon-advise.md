---
title: "IMSLogonAdvise"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMSLogon.Advise
api_type:
- COM
ms.assetid: a3c5d937-642b-463b-b5a0-5d099e651895
description: "Last modified: March 09, 2015"
---

# IMSLogon::Advise

  
  
**Applies to**: Outlook 
  
Registers an object with a message store provider for notifications about changes in the message store. The message store will then send notifications about changes to the registered object.
  
```cpp
HRESULT Advise(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulEventMask,
  LPMAPIADVISESINK lpAdviseSink,
  ULONG FAR * lpulConnection
);
```

## Parameters

 _cbEntryID_
  
> [in] The size, in bytes, of the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object about which notifications should be generated. This object can be a folder, a message, or any other object in the message store. Alternatively, if MAPI sets the  _cbEntryID_ parameter to 0 and passes **null** for  _lpEntryID_, the advise sink provides notifications about changes to the entire message store.
    
 _ulEventMask_
  
> [in] An event mask of the types of notification events occurring for the object about which MAPI will generate notifications. The mask filters specific cases. Each event type has a structure associated with it that contains additional information about the event. The following table lists the possible event types along with their corresponding structures.
    
|**Notification event type**|**Corresponding structure**|
|:-----|:-----|
|fnevCriticalError  <br/> |[ERROR_NOTIFICATION](error_notification.md) <br/> |
|fnevNewMail  <br/> |[NEWMAIL_NOTIFICATION](newmail_notification.md) <br/> |
|fnevObjectCreated  <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|fnevObjectDeleted  <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|fnevObjectModified  <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|fnevObjectCopied  <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|fnevObjectMoved  <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|fnevSearchComplete  <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|fnevStatusObjectModified  <br/> |[STATUS_OBJECT_NOTIFICATION](status_object_notification.md) <br/> |
   
 _lpAdviseSink_
  
> [in] A pointer to an advise sink object to be called when an event occurs for the session object about which notification has been requested. This advise sink object must already exist.
    
 _lpulConnection_
  
> [out] A pointer to a variable that upon a successful return holds the connection number for the notification registration. The connection number must be nonzero.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_SUPPORT 
  
> The operation is not supported by MAPI or by one or more service providers.
    
## Remarks

Message store providers implement the **IMSLogon::Advise** method to register an object for notification callbacks. Whenever a change occurs to the indicated object, the provider checks to see what event mask bit was set in the  _ulEventMask_ parameter and, therefore, what type of change occurred. If a bit is set, the provider calls the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for the advise sink object indicated by the  _lpAdviseSink_ parameter to report the event. Data passed in the notification structure to the **OnNotify** routine describes the event. 
  
The call to **OnNotify** can occur during the call that changes the object, or at any later time. On systems that support multiple threads of execution, the call to **OnNotify** can occur on any thread. To safely handle a call to **OnNotify** that might happen at an inopportune time, a client application should use the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function. 
  
To provide notifications, the message store provider that implements **Advise** needs to keep a copy of the pointer to the  _lpAdviseSink_ advise sink object; to do so, the provider calls the [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28v=VS.85%29.aspx) method for the advise sink to maintain its object pointer until notification registration is canceled with a call to the [IMSLogon::Unadvise](imslogon-unadvise.md) method. The **Advise** implementation should assign a connection number to the notification registration and call **AddRef** on this connection number before returning it in the  _lpulConnection_ parameter. Service providers can release the advise sink object before the registration is canceled, but they must not release the connection number until **Unadvise** has been called. 
  
After a call to **Advise** has succeeded and before **Unadvise** has been called, providers must be prepared for the advise sink object to be released. Therefore, a provider should release its advise sink object after **Advise** returns, unless it has a specific long-term use for it. 
  
For more information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). 
  
## See also



[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMSLogon::Unadvise](imslogon-unadvise.md)
  
[NOTIFICATION](notification.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)

