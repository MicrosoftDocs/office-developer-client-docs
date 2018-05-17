---
title: "UPDELE"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c38aa8be-ae77-0c40-9843-42e07b80db6b
description: "Last modified: July 23, 2011"
---

# UPDELE

  
  
**Applies to**: Outlook 
  
Extended information for items that have been deleted in a local store. This information is used during the [upload delete status state](upload-delete-status-state.md).
  
## Quick Info

```
struct UPDELE 
{ 
    ULONG ulFlags; 
    SKEY skey; 
    DWORD   dwReserved; 
    SBinary binChg; 
    SBinary binPcl; 
    SKEY skeyDst; 
    PUPMOV pupmov; 
};
```

## Members

 _ulFlags_
  
> [out]/[in] Flags to determine appropriate behavior during uploading.
    
    - UPD_ASSOC
    
  - [out] Item is associated.
    
    - UPD_MOV
    
  - [out] Item was moved out.
    
    -  UPD_OK 
    
  - [in] Upload was successful. The client sets this after uploading information to server.
    
    - UPD_MOVED
    
  - [in] Item was moved successfully.
    
    - UPD_UPDATE
    
  - [in] Mark source item as modified.
    
    - UPD_COMMIT
    
  - [in] Commit upload state now (entry 0).
    
 _skey_
  
> [out] Source key of item.
    
 _dwReserved_
  
> [out] This member is reserved for the internal use of Outlook and is not supported.
    
 _binChg_
  
> [out] Change key of destination item if item has been moved.
    
 _binPcl_
  
> [out] Change list of destination item if item has been moved.
    
 _skeyDst_
  
> [out] Source key of destination item if item has been moved.
    
 _pupmov_
  
> [out] Destination folder information if item has been moved.
    
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)
  
[SKEY](skey.md)
  
[UPDEL](updel.md)
  
[UPMOV](upmov.md)

