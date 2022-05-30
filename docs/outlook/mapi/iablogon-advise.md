---
title: "IABLogonAdvise"
description: Describes IABLogonAdvise provides syntax, parameters, and return value.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IABLogon.Advise
api_type:
- COM
ms.assetid: 375d65b1-607d-4e2a-8052-9bcbf08fc2ac
---

# IABLogon::Advise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Registers the caller to receive notification of specified events that affect a container, messaging user, or distribution list.
  
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
  
> [in] The count of bytes in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object about which notifications should be generated.
    
 _ulEventMask_
  
> [in] A bitmask of values that indicate the types of notification events that the caller is interested in and should be included in the registration. There is a corresponding [NOTIFICATION](notification.md) structure associated with each type of event that holds information about the event. The following table lists the valid values for the  _ulEventMask_ parameter and the structures associated with each value. 
    
|**Notification event type**|**Corresponding **NOTIFICATION** structure**|
|:-----|:-----|
|**fnevCriticalError** <br/> |[ERROR_NOTIFICATION](error_notification.md) <br/> |
|**fnevObjectCreated** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectDeleted** <br/> |**OBJECT_NOTIFICATION** <br/> |
|**fnevObjectModified** <br/> |**OBJECT_NOTIFICATION** <br/> |
|**fnevObjectCopied** <br/> |**OBJECT_NOTIFICATION** <br/> |
|**fnevObjectMoved** <br/> |**OBJECT_NOTIFICATION** <br/> |
   
 _lpAdviseSink_
  
> [in] A pointer to an advise sink object to receive the subsequent notifications.
    
 _lpulConnection_
  
> [out] A pointer to a nonzero value that represents the notification registration.
    
## Return value

S_OK 
  
> The notification registration was successful.
    
MAPI_E_INVALID_ENTRYID 
  
> The entry identifier passed in the _lpEntryID_ parameter is not in the appropriate format. 
    
MAPI_E_NO_SUPPORT 
  
> The address book provider does not support notification, possibly because it does not allow changes to be made to its objects.
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The address book provider cannot handle the entry identifier passed in  _lpEntryID_.
    
## Remarks

Address book providers implement the **IABLogon::Advise** method to register the caller to be notified when a change occurs to an object in one of their containers. Callers can register for notifications regarding messaging users, distribution lists, or entire containers. 
  
Clients typically call the [IAddrBook::Advise](iaddrbook-advise.md) method to register for address book notifications. MAPI then calls the **Advise** method of the address book provider that is responsible for the object represented by the entry identifier in  _lpEntryID_.
  
When a change occurs to the indicated object of the type represented in  _ulEventMask_, a call is made to the **OnNotify** method of the advise sink pointed to by  _lpAdviseSink_. Data passed in the **NOTIFICATION** structure to the **OnNotify** routine describes the event. 
  
## Notes to implementers

You can support notification with or without help from MAPI. MAPI has three support object methods to help service providers implement notification:
  
- [IMAPISupport::Subscribe](imapisupport-subscribe.md)
    
- [IMAPISupport::Unsubscribe](imapisupport-unsubscribe.md)
    
- [IMAPISupport::Notify](imapisupport-notify.md)
    
If you elect to use the MAPI support methods, call **Subscribe** when your **Advise** method is called and release the  _lpAdviseSink_ pointer. 
  
If you elect to support notification yourself, call the **AddRef** method of the advise sink represented by the  _lpAdviseSink_ parameter to keep a copy of this pointer. Maintain this copy until your [IABLogon::Unadvise](iablogon-unadvise.md) method is called to cancel the registration. 
  
Regardless of how you support notification, assign a nonzero connection number to the notification registration and return it in the _lpulConnection_ parameter. Do not release this connection number until the **Unadvise** method has been called. 
  
## Notes to callers

The advise sink pointer that you pass in the _lpAdviseSink_ parameter to **Advise** can point to an object that you have created or that MAPI has created through the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function. You might want to use **HrThisThreadAdviseSink** if you support multiple threads of execution and want to be sure that that subsequent calls to your **OnNotify** method occur at an appropriate time on an appropriate thread. 
  
Be prepared for your advise sink object to be released any time after your call to **Advise** and before your call to **Unadvise**. Therefore, you should release your advise sink object after **Advise** returns, unless you have a specific long-term use for it. 
  
For more information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). For information about how to use the **IMAPISupport** methods to support notification, see [Supporting Event Notification](supporting-event-notification.md). For more information about multithreading and MAPI, see [Threading in MAPI](threading-in-mapi.md).
  
## See also



[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IABLogon::Unadvise](iablogon-unadvise.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[NOTIFICATION](notification.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

