---
title: "UPREADE"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d146ee74-0c3a-5fdd-b1aa-af6498550801
description: "Last modified: July 23, 2011"
---

# UPREADE

**Applies to**: Outlook 
  
Extended information for uploading the read state of an item during the [upload read status state](upload-read-status-state.md).
  
## Quick Info

```cpp
struct UPREADE 
{ 
    ULONG ulFlags; 
    SKEY skey; 
};
```

## Members

_ulFlags_
  
>  [out]/[in] Flags to determine the appropriate behavior during the upload. 
    
  - UPR_ASSOC
    
    - [out] Item is hidden.
    
  - UPR_READ
    
    - [out] The read status of the item has been changed.
    
  - UPR_OK
    
    - [in] Upload was successful. The client sets this after uploading information to the server.
    
  - UPR_COMMIT
    
    - [in] Upload the read status of the item now, instead of waiting to the end of the [upload table state](upload-table-state.md) to batch-process more than one item. 
    
_skey_
  
> [out] Source key of the item.
    
## See also

- [About the Replication API](about-the-replication-api.md)
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)
- [UPREAD](upread.md)

