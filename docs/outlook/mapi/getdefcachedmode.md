---
title: "GetDefCachedMode"
description: Describes GetDefCachedMode and provides syntax, parameters, and return value.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 325b6b47-b6a6-503e-e9bb-65ef7b73d659
---

# GetDefCachedMode

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates whether Cached Exchange Mode for the private Exchange store is enabled, and whether this is enforced by policy.
  
## Quick info

|Property|Value|
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

