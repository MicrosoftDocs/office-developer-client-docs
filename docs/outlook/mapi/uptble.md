---
title: "UPTBLE"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: f7fcb385-186d-d5fe-7104-fe0af09d5768
description: "Last modified: July 23, 2011"
---

# UPTBLE

**Applies to**: Outlook 2013 | Outlook 2016 
  
Extended information for uploading the contents of a folder during the [upload table state](upload-table-state.md).
  
## Quick info

```cpp
struct UPTBLE 
{ 
    UINTiEntMod; 
    UINTcEntMod; 
    UINTiEntRead; 
    UINTcEntRead; 
    UINTiEntDel; 
    UINTcEntDel; 
};
```

## Members

 _iEntMod_
  
>  [out] Index to track uploading the  _cEntMod_ number of new or modified items. 
    
 _cEntMod_
  
>  [out] Number of new or modified items in the folder. 
    
 _iEntRead_
  
>  [out] Index to track uploading the number of  _cEntRead_ read items. 
    
 _cEntRead_
  
>  [out] Number of read items in the folder. 
    
 _iEntDel_
  
>  [out] Index to track uploading the number of  _cEntDel_ deleted items. 
    
 _cEntDel_
  
>  [out] Number of deleted items in the folder. 
    
## See also

- [About the Replication API](about-the-replication-api.md) 
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [UPTBL](uptbl.md)

