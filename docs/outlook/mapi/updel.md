---
title: "UPDEL"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b23291d-3355-d772-4647-d4bbd64b0b53
description: "Last modified: July 23, 2011"
---

# UPDEL

  
  
**Applies to**: Outlook 
  
Information for items that have been deleted in a local store. This information is used during the [upload delete status state](upload-delete-status-state.md).
  
## Quick info

```cpp
struct UPDEL 
{ 
    PUPDELE pupde; 
    UINT cEnt; 
};
```

## Members

 _pupde_
  
>  [out] Vector of [UPDELE](updele.md) entries. 
    
 _cEnt_
  
> [out] Number of entries in  *pupde*  . 
    
## See also



[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)

