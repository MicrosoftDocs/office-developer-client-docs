---
title: "GetDefCachedModeDownloadPubFoldFavs"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2dd95561-ed8f-8a3b-6532-b53556f16666
description: "Last modified: March 09, 2015"
---

# GetDefCachedModeDownloadPubFoldFavs

  
  
**Applies to**: Outlook 
  
Indicates whether Cached Exchange Mode for the **Public Folder Favorites** folder is enabled, and whether this is enforced by policy. 
  
## Quick info

|||
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
    
## Return Values

 **true**
  
- Caching is enabled.
    
 **false**
  
- Caching is disabled.
    
## See also



[GetDefCachedMode](getdefcachedmode.md)

