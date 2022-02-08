---
title: "IMAPISessionAdvise"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.Advise
api_type:
- COM
ms.assetid: a6a6b6b1-31e2-4899-a5fe-74d5d1c2ccfc
description: "Last modified: March 09, 2015"
---

# IMAPISession::Advise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Registers to receive notification of specified events that affect the session.
  
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
  
> [in] A pointer to the entry identifier of the address book or message store object about which notifications should be generated, or NULL, which indicates that the client is registering to receive notifications about events that affect only the session. 
    
 _ulEventMask_
  
> [in] A mask of values that indicate the types of notification events that the client is interested in and should be included in the registration. If  _lpEntryID_ is NULL, MAPI automatically registers the client for critical error events that affect only the session. When  _lpEntryID_ points to an entry identifier, the following values are valid for the  _ulEventMask_ parameter: 
    
fnevCriticalError 
  
> Registers for notifications about severe errors, such as insufficient memory.
    
fnevExtended 
  
> Registers for notifications about events specific to a particular address book or message store provider and about session shut down.
    
fnevNewMail 
  
> Registers for notifications about the arrival of new messages. 
    
fnevObjectCreated 
  
> Registers for notifications about the creation of a new object.
    
fnevObjectCopied
  
> Registers for notifications about an object being copied.
    
fnevObjectDeleted
  
> Registers for notifications about an object being deleted.
    
fnevObjectModified
  
> Registers for notifications about an object being modified.
    
fnevObjectMoved
  
> Registers for notifications about an object being moved.
    
fnevSearchComplete
  
> Registers for notifications about the completion of a search operation.
    
 _lpAdviseSink_
  
> [in] A pointer to an advise sink object to receive the subsequent notifications. This advise sink object must have already been allocated.
    
 _lpulConnection_
  
> [out] A pointer to a nonzero number that represents the connection between the caller's advise sink object and the session.
    
## Return value

S_OK 
  
> The registration was successful.
    
MAPI_E_INVALID_ENTRYID 
  
> The entry identifier pointed to by  _lpEntryID_ does not represent a valid entry identifier. 
    
MAPI_E_NO_SUPPORT 
  
> The service provider responsible for the entry identifier pointed to by  _lpEntryID_ either does not support the type of events specified in the _ulEventMask_ parameter or does not support notification. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier pointed to by  _lpEntryID_ cannot be handled by any of the service providers in the profile. 
    
## Remarks

The **IMAPISession::Advise** method establishes a connection between the caller's advise sink object, the session and, optionally, a service provider. This connection is used to send notifications to the advise sink when one or more events specified in the _ulEventMask_ parameter occur to the object pointed to by  _lpEntryID_. When  _lpEntryID_ is NULL, the target object is the session and notifications are sent only for critical errors and extended events. 
  
When  _lpEntryID_ points to a valid entry identifier, MAPI calls the **Advise** method of the logon object that belongs to the responsible service provider. For example, if  _lpEntryID_ points to the entry identifier of a distribution list, MAPI calls the appropriate address book provider's [IABLogon::Advise](iablogon-advise.md) method. 
  
To send a notification, either the service provider or MAPI calls the registered advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method. One of the parameters to **OnNotify**, a notification structure, contains information that describes the specific event.
  
## Notes to callers

On systems that support multiple threads of execution, the call to **OnNotify** can also occur on any thread at any time. If you need assurance that notifications will occur only at a particular time on a particular thread, call the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function to generate the advise sink object that you pass to the **Advise** method. 
  
To determine when a client has logged off, register for notifications in your service provider by calling **Advise** with  _lpEntryID_ set to NULL and  _cbEntryID_ set to 0. When the logoff occurs, you will receive an fnevExtended notification. 
  
After a call to **Advise** has succeeded and before [IMAPISession::Unadvise](imapisession-unadvise.md) has been called to cancel the registration, release your advise sink object unless you have a specific long-term use for it. 
  
For an overview of the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). 
  
For more information about handling notifications, see [Handling Notifications](handling-notifications.md). 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|BaseDialog.cpp  <br/> |CBaseDialog::OnNotificationsOn  <br/> |MFCMAPI uses the **IMAPISession::Advise** method to register for notifications against the session.  <br/> |
   
## See also



[IABLogon::Advise](iablogon-advise.md)
  
[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMAPISession::Unadvise](imapisession-unadvise.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Event Notification in MAPI](event-notification-in-mapi.md)

