---
title: "IMAPIOfflineSetCurrentState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIOffline.SetCurrentState
api_type:
- COM
ms.assetid: c0aa0df2-79f9-2558-7eb6-accae9bef4b2
description: "Last modified: July 23, 2011"
---

# IMAPIOffline::SetCurrentState

  
  
**Applies to**: Outlook 
  
Sets the current state of an offline object to online or offline.
  
```
HRESULT SetCurrentState( 
    ULONG ulFlags, 
    ULONG ulMask, 
    ULONG ulState, 
    void* pReserved 
);
```

## Parameters

 _ulFlags_
  
> [in] Modifies the behavior of this call. The supported values are:
    
MAPIOFFLINE_FLAG_BLOCK
  
> Setting  _ulFlags_ to this value will block the **SetCurrentState** call until the state change is complete. By default the transition takes place asynchronously. When the transition is occuring asynchronously, all **SetCurrentState** calls will return **E_PENDING** until the change is complete. 
    
MAPIOFFLINE_FLAG_DEFAULT
  
> Sets the current state without blocking.
    
 _ulMask_
  
> [in] The part of the state to change. The only supported value is MAPIOFFLINE_STATE_OFFLINE_MASK.
    
 _ulState_
  
> [in] The state to change to. It must be one of these two values:
    
MAPIOFFLINE_STATE_ONLINE
  
> 
    
MAPIOFFLINE_STATE_OFFLINE
  
> 
    
 _pReserved_
  
> This parameter is reserved for Outlook internal use and is not supported. 
    
## Return value

S_OK
  
> The state of the offline object has been changed successfully.
    
E_PENDING
  
> This indicates that the state of the offline object is changing asynchronously. This occurs when  _ulFlags_ is set to MAPIOFFLINE_FLAG_BLOCK in an earlier **SetCurrentState** call, and any subsequent **SetCurrentState** call will return this value until the asynchronous state change is complete. 
    
## See also

#### Reference

[IMAPIOffline::GetCapabilities](imapioffline-getcapabilities.md)
  
[IMAPIOffline::GetCurrentState](imapioffline-getcurrentstate.md)
#### Concepts

[MAPI Constants](mapi-constants.md)

