---
title: "IMAPIOfflineGetCurrentState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOffline.GetCurrentState
api_type:
- COM
ms.assetid: f3769e83-d678-1087-fc0f-b4f156386333
description: "Last modified: July 23, 2011"
---

# IMAPIOffline::GetCurrentState

  
  
**Applies to**: Outlook 
  
Gets the current online or offline state of an offline object.
  
```
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

#### Reference

[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)
  
[IMAPIOffline::SetCurrentState](imapioffline-setcurrentstate.md)
#### Concepts

[MAPI Constants](mapi-constants.md)

