---
title: "GetDefCachedModeDownloadPubFoldFavs"
description: Describes GetDefCachedModeDownloadPubFoldFavs and provides syntax, parameters, and return value.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 2dd95561-ed8f-8a3b-6532-b53556f16666
---

# GetDefCachedModeDownloadPubFoldFavs

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates whether Cached Exchange Mode for the **Public Folder Favorites** folder is enabled, and whether this is enforced by policy. 
  
## Quick info

|Property|Value|
|:-----|:-----|
|Exported by:  <br/> |msmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
   
```cpp
BOOL GetDefCachedModeDownloadPubFoldFavs(BOOL *pfPolicy); 

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



[GetDefCachedMode](getdefcachedmode.md)

