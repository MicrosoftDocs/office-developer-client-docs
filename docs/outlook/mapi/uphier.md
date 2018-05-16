---
title: "UPHIER"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a75ca0dd-9c50-2a9f-6c59-1f8020833a01
description: "Last modified: July 23, 2011"
---

# UPHIER

  
  
**Applies to**: Outlook 
  
Information for synchronizing a folder hierarchy during the [upload hierarchy state](upload-hierarchy-state.md).
  
## Quick Info

```
struct UPHIER 
{ 
    ULONG ulFlags; 
    LPSTREAM pstmReserved; 
    UINT iEnt; 
    UINT cEnt; 
};
```

## Members

 _ulFlags_
  
> [in] Flags to modify the behavior when synchronizing the folder hierarchy.
    
    - UPH_OK
    
  - [in] Upload was successful. The client sets this after successfully uploading information to the server. Upon seeing this flag, Outlook clears any internal bookkeeping information that indicated the folder hierarchy needed updating. 
    
    - The client passes the HRESULT if the upload was not successful.
    
 _pstmReserved_
  
> [out] This member is reserved for Outlook internal use and is not supported.
    
 _iEnt_
  
> [out] Index to track synchronizing the number of folders specified by  *cEnt*  . 
    
 _cEnt_
  
> [out] Number of folders that are out of sync.
    
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)

