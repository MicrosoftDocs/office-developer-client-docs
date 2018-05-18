---
title: "NOTIFCALLBACK"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.NOTIFCALLBACK
api_type:
- COM
ms.assetid: 416008b4-13aa-4387-8c12-f8f2ca252391
description: "Last modified: March 09, 2015"
---

# NOTIFCALLBACK

  
  
**Applies to**: Outlook 
  
Defines a callback function that MAPI calls to send an event notification. This callback function can only be used when wrapped in an advise sink object created by calling the [HrAllocAdviseSink](hrallocadvisesink.md) function. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Defined function implemented by:  <br/> |Client applications and service providers  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
   
```cpp
ULONG (STDAPICALLTYPE NOTIFCALLBACK)(
  LPVOID lpvContext,
  ULONG cNotification,
  LPNOTIFICATION lpNotifications
);
```

## Parameters

 _lpvContext_
  
> [in] Pointer to an arbitrary value passed to the callback function when MAPI calls it. This value can represent an address of significance to the client application or service provider. Typically, for C++ code, the  _lpvContext_ parameter represents a pointer to a C++ object. 
    
 _cNotification_
  
> [in] Count of event notifications in the array indicated by the  _lpNotifications_ parameter. 
    
 _lpNotifications_
  
> [out] Pointer to the location where this function writes an array of [NOTIFICATION](notification.md) structures that contains the event notifications. 
    
## Return value

The set of valid return values for the **NOTIFCALLBACK** function prototype depends on whether the function is implemented by a client application or a service provider. Clients should always return S_OK. Providers can return either S_OK or CALLBACK_DISCONTINUE. 
  
## Remarks

CALLBACK_DISCONTINUE is a valid return value for synchronous callback functions only; it requests that MAPI immediately stop processing the callbacks for this notification. When CALLBACK_DISCONTINUE is returned, MAPI sets the  _lpUlFlags_ parameter to NOTIFY_CANCELED when it returns from [IMAPISupport::Notify](imapisupport-notify.md). 
  
The following are limitations on what a synchronous callback function can do:
  
- It cannot cause another synchronous notification to be generated.
    
- It cannot display a user interface.
    
## See also

#### Reference

[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)

