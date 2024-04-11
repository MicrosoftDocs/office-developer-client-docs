---
title: "IMAPIOfflineGetCurrentState"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIOffline.GetCurrentState
api_type:
- COM
ms.assetid: f3769e83-d678-1087-fc0f-b4f156386333
---

# IMAPIOffline::GetCurrentState

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Gets the current online or offline state of an offline object.
  
```cpp
HRESULT GetCurrentState( 
    ULONG* pulState 
);
```

## Parameters

 _pulState_
  
> [out] The current online or offline state of an offline object. It must be one of these two values:
    
MAPIOFFLINE_STATE_ONLINE
  
> 
    
MAPIOFFLINE_STATE_OFFLINE
  
> 
    
## See also



[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)
  
[IMAPIOffline::SetCurrentState](imapioffline-setcurrentstate.md)


[MAPI Constants](mapi-constants.md)

