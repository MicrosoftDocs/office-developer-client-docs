---
title: "IMAPITableUnadvise"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.Unadvise
api_type:
- COM
ms.assetid: 19f0dad9-9704-4bbe-a689-9531e7198351
description: "Last modified: March 09, 2015"
---

# IMAPITable::Unadvise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Cancels the sending of notifications previously set up with a call to the [IMAPITable::Advise](imapitable-advise.md) method. 
  
```cpp
HRESULT Unadvise(
ULONG_PTR ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] The number of the registration connection returned by a call to [IMAPITable::Advise](imapitable-advise.md).
    
## Return value

S_OK 
  
> The call succeeded.
    
## Remarks

Use the **IMAPITable::Unadvise** method to release the pointer to the advise sink object passed in the _lpAdviseSink_ parameter in the previous call to **IMAPITable::Advise**, thereby canceling a notification registration. As part of discarding the pointer to the advise sink object, the object's **IUnknown::Release** method is called. Generally, **Release** is called during the **Unadvise** call, but if another thread is in the process of calling the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for the advise sink, the **Release** call is delayed until the **OnNotify** method returns. 
  
For more information on the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). For specific information about table notification, see [About Table Notifications](about-table-notifications.md). For information about using the **IMAPISupport** methods to support notification, see [Supporting Event Notification](supporting-event-notification.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::NotificationOff  <br/> |MFCMAPI uses the **IMAPITable::Unadvise** method to cancel notifications for the table.  <br/> |
   
## See also



[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMAPITable::Advise](imapitable-advise.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

