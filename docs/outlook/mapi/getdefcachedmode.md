---
title: "GetDefCachedMode"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 325b6b47-b6a6-503e-e9bb-65ef7b73d659
description: "Last modified: March 09, 2015"
---

# GetDefCachedMode

  
  
**Applies to**: Outlook 
  
Indicates whether Cached Exchange Mode for the private Exchange store is enabled, and whether this is enforced by policy.
  
## Quick info

|||
|:-----|:-----|
|Exported by:  <br/> |msmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
   
```cpp
BOOL GetDefCachedMode(BOOL *pfPolicy); 

```

## Parameters

 _pfPolicy_
  
> [out] **true** if the return value is enforced by policy, **false** if it is not. 
    
## Return values

 **true**
  
- Caching is enabled.
    
 **false**
  
- Caching is disabled.
    
## See also



[GetDefCachedModeDownloadPubFoldFavs](getdefcachedmodedownloadpubfoldfavs.md)

