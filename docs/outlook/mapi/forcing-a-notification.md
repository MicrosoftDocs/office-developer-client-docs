---
title: "Forcing a Notification"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9c7d6605-73ee-468c-981b-e0853106c9ba
description: "Last modified: July 23, 2011"
 
 
---

# Forcing a Notification

  
  
**Applies to**: Outlook 
  
When service providers use the [IMAPISupport : IUnknown](imapisupportiunknown.md) methods for notification, MAPI delivers notifications using a hidden window and its corresponding window procedure. For each process to receive a notification, MAPI posts a special message to the hidden window. This message is named with the constant **szMAPINotificationMsg** which is defined in MAPIDEFS.H. 
  
You receive these notifications when the hidden window's window procedure processes the **szMAPINotificationMsg** message. To guarantee that notifications are delivered, it is necessary to wait for and dispatch this **szMAPINotificationMsg** message. Implementing the logic to achieve this can be done fairly simply, but MAPI provides an entry point into the MAPI DLL called [HrDispatchNotifications](hrdispatchnotifications.md) to make processing even simpler. Call **HrDispatchNotifications** as follows to receive notifications in your client: 
  
```cpp
HRESULT hr = HrDispatchNotifications(0);
 
```


