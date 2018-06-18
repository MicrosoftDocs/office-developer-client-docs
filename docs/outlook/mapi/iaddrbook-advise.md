---
title: "IAddrBookAdvise"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.Advise
api_type:
- COM
ms.assetid: 2def89ed-e4ce-446a-8b80-132d11ae8f8b
description: "Last modified: March 09, 2015"
---

# IAddrBook::Advise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Registers a client or service provider to receive notifications about changes to one or more entries in the address book.
  
```cpp
HRESULT Advise(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulEventMask,
  LPMAPIADVISESINK lpAdviseSink,
  ULONG_PTR lpulConnection
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the address book container, messaging user, or distribution list that will generate a notification when a change occurs of the type or types described in the  _ulEventMask_ parameter. 
    
 _ulEventMask_
  
> [in] One or more notification events that the caller is registering to receive. Each event is associated with a particular notification structure that contains information about the change that occurred. The following table lists the valid values for  _ulEventMask_ and their corresponding structures. 
    
|**Notification event**|**Corresponding structure**|
|:-----|:-----|
|**fnevCriticalError** <br/> |[ERROR_NOTIFICATION](error_notification.md) <br/> |
|**fnevObjectCreated** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectDeleted** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectModified** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectCopied** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectMoved** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevTableModified** <br/> |[TABLE_NOTIFICATION](table_notification.md) <br/> |
   
 _lpAdviseSink_
  
> [in] A pointer to the advise sink object to be called when the event for which notification has been requested occurs.
    
 _lpulConnection_
  
> [out] A pointer to a nonzero connection number that represents the notification registration.
    
## Return value

S_OK 
  
> The notification registration was successful.
    
MAPI_E_INVALID_ENTRYID 
  
> The address book provider responsible for the entry identifier passed in  _lpEntryID_ could not register a notification for the corresponding entry. 
    
MAPI_E_NO_SUPPORT 
  
> Notification is not supported by the address book provider responsible for the object identified by the entry identifier passed in the  _lpEntryID_ parameter. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier passed in  _lpEntryID_ cannot be handled by any of the address book providers in the profile. 
    
## Remarks

Clients and service providers call the **Advise** method to register for a particular type or types of notification on an address book entry. The types of notification are indicated by the event mask passed in with the  _ulEventMask_ parameter. 
  
MAPI forwards this **Advise** call to the address book provider that is responsible for the entry as indicated by the entry identifier in the  _lpEntryID_ parameter. The address book provider either handles the registration itself or calls the support method, [IMAPISupport::Subscribe](imapisupport-subscribe.md), to prompt MAPI to register the caller. A nonzero connection number is returned to represent the successful registration.
  
Whenever a change occurs to the entry of the type indicated by the notification registration, the address book provider calls the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for the advise sink object specified in the  _lpAdviseSink_ parameter. The **OnNotify** method includes a [NOTIFICATION](notification.md) structure as an input parameter that contains data to describe the event. 
  
Depending on the address book provider, the call to **OnNotify** can occur immediately following the change to the registered object or at a later time. On systems that support multiple threads of execution, the call to **OnNotify** can occur on any thread. Clients can request that these notifications occur on a particular thread by calling the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function to create the advise sink object that is passed to **Advise**. 
  
Because an address book provider can release the advise sink object passed in by clients at any time after the successful completion of the **Advise** call and before an [IAddrBook::Unadvise](iaddrbook-unadvise.md) call to cancel the notification, clients should release their advise sink objects when **Advise** returns. 
  
For more information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md).
  
## See also



[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IAddrBook::Unadvise](iaddrbook-unadvise.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[NOTIFICATION](notification.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

