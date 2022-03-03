---
title: "IPSTX2SetSpoolSuspendState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IPSTX2.SetSpoolSuspendState
api_type:
- COM
ms.assetid: 396db029-1d4a-203d-2256-3353d03c6767
---

# IPSTX2::SetSpoolSuspendState

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the suspended state on the spooler.
  
```cpp
void SetSpoolSuspendState( 
    ULONG ulState 
);
```

## Parameters

 _ulState_
  
> [in] The state to set the spooler to. It must be one of the following values:
    
 **SS_ACTIVE**
  
> 
    
 **SS_SUSPENDED**
  
> 
    
## See also



[MAPI Constants](mapi-constants.md)

