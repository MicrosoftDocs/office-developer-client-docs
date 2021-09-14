---
title: "HrDispatchNotifications"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HrDispatchNotifications
api_type:
- COM
ms.assetid: 42ec4266-67b9-416e-8b9b-163c95011626
description: "Last modified: March 09, 2015"
---

# HrDispatchNotifications

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Forces dispatching of all queued notifications. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrDispatchNotifications(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero. 
    
## Return value

S_OK
  
> All queued notifications have been dispatched.
    
MAPI_E_USER_CANCEL
  
> WM_QUIT, WM_QUERYENDSESSION, or WM_ENDSESSION was received.
    
MAPI_E_NOT_INITIALIZED
  
> MAPI was not initialized.
    
## Remarks

The **HrDispatchNotifications** function causes MAPI to dispatch all notifications that are currently queued in the MAPI notification engine without waiting for a message dispatch. This can have a beneficial effect on memory utilization. For more information, see [Forcing a Notification](forcing-a-notification.md). 
  
## Notes to callers

Some applications wait for a notification message in a timeout loop using the Windows [PeekMessage](https://msdn.microsoft.com/library/ms644943.aspx) and [DispatchMessage](https://msdn.microsoft.com/library/ms644934.aspx) functions. On all but the fastest platforms, such applications might experience poor performance or even blockage of notifications. Using **HrDispatchNotifications** not only reduces code but improves performance. 
  

