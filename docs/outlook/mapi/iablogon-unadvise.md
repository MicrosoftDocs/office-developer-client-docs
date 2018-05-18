---
title: "IABLogonUnadvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABLogon.Unadvise
api_type:
- COM
ms.assetid: 3e506b29-c7e3-40d6-a08b-22fa87088c2d
description: "Last modified: July 23, 2011"
---

# IABLogon::Unadvise

  
  
**Applies to**: Outlook 
  
Cancels notifications that were previously set up with a call to the [IABLogon::Advise](iablogon-advise.md) method. 
  
```cpp
HRESULT Unadvise(
  ULONG ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] The connection number associated with an active notification registration. A previous call to **Advise** must have returned the value of  _ulConnection_.
    
## Return value

S_OK 
  
> The notification registration was successfully canceled.
    
## Remarks

MAPI calls the **Unadvise** method to cancel a notification registration for a container, messaging user, or distribution list object. 
  
## Notes to Implementers

Your implementation of **Unadvise** will depend on whether you support notification with MAPI's help or manually. If MAPI provides your support, call the [IMAPISupport::Unsubscribe](imapisupport-unsubscribe.md) method to cancel the registration. If another thread is in the process of calling the advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method, it can be delayed until **OnNotify** has returned. 
  
For more information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). For information about how to use the [IMAPISupport : IUnknown](imapisupportiunknown.md) methods to support notification, see [Supporting Event Notification](supporting-event-notification.md).
  
## See also

#### Reference

[IABLogon::Advise](iablogon-advise.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

