---
title: "IMAPIOfflineGetCapabilities"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOffline.GetCapabilities
api_type:
- COM
ms.assetid: aa8dc48b-9e1c-8da0-9579-10b7174e99de
description: "Last modified: July 23, 2011"
---

# IMAPIOffline::GetCapabilities

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Gets the conditions for which callbacks are supported by an offline object.
  
```cpp
HRESULT GetCapabilities( 
    ULONG *pulCapabilities 
);
```

## Parameters

 _pulCapablities_
  
> [out] A bitmask of the following capability flags:
    
MAPIOFFLINE_CAPABILITY_OFFLINE
  
> The offline object is capable of providing offline notifications.
    
MAPIOFFLINE_CAPABILITY_ONLINE
  
> The offline object is capable of providing online notifications.
    
## Remarks

Upon opening an offline object using **[HrOpenOfflineObj](hropenofflineobj.md)**, a client can query on [IMAPIOfflineMgr](imapiofflinemgrimapioffline.md) to obtain a pointer to an **IMAPIOffline** interface, and call **IMAPIOffline::GetCapabilities** to find out the callbacks supported by the object. The client can then choose to set up callbacks by using **IMAPIOfflineMgr**.
  
Note that, depending on the mail server for an offline object, an object that supports callbacks for going online does not necessarily support callbacks for going offline.
  
Also note that, while an offline object may support callbacks for changes other than online/offline, the Offline State API supports only online/offline changes, and clients must check for only such capabilities.
  
## See also



[IMAPIOffline::GetCurrentState](imapioffline-getcurrentstate.md)
  
[IMAPIOffline::SetCurrentState](imapioffline-setcurrentstate.md)
  
[IMAPIOfflineMgr : IMAPIOffline](imapiofflinemgrimapioffline.md)


[MAPI Constants](mapi-constants.md)
  
[HrOpenOfflineObj](hropenofflineobj.md)

