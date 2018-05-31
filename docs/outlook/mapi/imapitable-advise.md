---
title: "IMAPITableAdvise"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.Advise
api_type:
- COM
ms.assetid: e8b5d21e-dc14-4b61-96b3-a51bcfa0d232
description: "Last modified: March 09, 2015"
---

# IMAPITable::Advise

  
  
**Applies to**: Outlook 
  
Registers an advise sink object to receive notification of specified events affecting the table.
  
```cpp
HRESULT Advise(
ULONG ulEventMask,
LPMAPIADVISESINK lpAdviseSink,
ULONG_PTR FAR * lpulConnection
);
```

## Parameters

 _ulEventMask_
  
> [in] Value indicating the type of event that will generate the notification. Only the following value is valid:
    
 `fnevTableModified`
  
 _lpAdviseSink_
  
> [in] Pointer to an advise sink object to receive the subsequent notifications. This advise sink object must have been already allocated.
    
 _lpulConnection_
  
> [out] Pointer to a nonzero value that represents the successful notification registration.
    
## Return value

S_OK 
  
> The notification registration successfully completed.
    
MAPI_E_NO_SUPPORT 
  
> The table implementation either does not support changes to its rows and columns or does not support notification.
    
## Remarks

Use the **IMAPITable::Advise** method to register a table object implemented in the provider for notification callbacks. Whenever a change occurs to the table object, the provider checks to see what event mask bit was set in the  _ulEventMask_ parameter and thus what type of change occurred. If a bit is set, then the provider calls the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for the advise sink object indicated by the  _lpAdviseSink_ parameter to report the event. Data passed in the notification structure to the **OnNotify** routine describes the event. 
  
The call to **OnNotify** can occur during the call that changes the object, or at any following time. On systems that support multiple threads of execution, the call to **OnNotify** can occur on any thread. For a way to turn a call to **OnNotify** that might happen at an inopportune time into one that is safer to handle, a provider should use the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function. 
  
To provide notifications, the provider implementing **Advise** needs to keep a copy of the pointer to the  _lpAdviseSink_ advise sink object; to do so, it calls the **IUnknown::AddRef** method for the advise sink to maintain its object pointer until notification registration is canceled with a call to the [IMAPITable::Unadvise](imapitable-unadvise.md) method. The **Advise** implementation should assign a connection number to the notification registration and call **AddRef** on this connection number before returning it in the  _lpulConnection_ parameter. Service providers can release the advise sink object before the registration is canceled, but they must not release the connection number until ** Unadvise ** has been called. 
  
After a call to **Advise** has succeeded and before ** Unadvise ** has been called, clients must be prepared for the advise sink object to be released. A client should therefore release its advise sink object after **Advise** returns unless it has a specific long-term use for it. 
  
Because of the asynchronous behavior of notification, implementations that change table column settings can receive notifications with information organized in a previous column order. For instance, a table row might be returned for a message that has just been deleted from the container. Such a notification is sent when the column setting change has been made and information about it sent but the notification table view has not been updated with that information yet.
  
For more information on the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). For specific information about table notification, see [About Table Notifications](about-table-notifications.md). For information about using the **IMAPISupport** methods to support notification, see [Supporting Event Notification](supporting-event-notification.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContestTableListCtrl::NotificationOn  <br/> |MFCMAPI uses the **IMAPITable::Advise** method to register for notifications to allow the table view to stay current.  <br/> |
   
## See also



[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMAPITable::Unadvise](imapitable-unadvise.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

