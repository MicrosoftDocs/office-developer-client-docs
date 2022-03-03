---
title: "UPTBL"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 39d9ad3b-ff4b-8378-a3ac-d5621c7ef7f1
---

# UPTBL

**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for uploading the contents of a folder during the [upload table state](upload-table-state.md).
  
## Quick info

```cpp
struct UPTBL 
{ 
    ULONG ulFlags; 
    LPSTREAM pstmReserved; 
    LPSTR pszName; 
    FEID feid; 
    UINT uintReserved; 
    UPTBLE rgte[2]; 
    UINT iEnt; 
    UINT cEnt; 
    PUPMOV pupmovHead; 
    void* pReserved; 
};
```

## Members

_ulFlags_
  
> [in] Flags to determine the appropriate behavior during the upload.
    
  - UPT_OK
    
    - [in] Upload was successful. The client sets this after uploading the folder contents to the server.
    
_pstmReserved_
  
> [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pszName_
  
> [out] Name of the folder.
    
_feid_
  
> [out] Entry ID of the folder.
    
_uintReserved_
  
> [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_rgte_
  
> [out] Structure to hold the following information for normal (or non-hidden) items and associated (or hidden) items in the folder:  _rgte[0]_ is for normal items, and  _rgte[1]_ is for associated items. 
    
   - the number of new or modified items
   - the number of read items 
   - the number of deleted items
    
 _iEnt_
  
> [out] Index to track uploading the number of changes specified by  _cEnt_.
    
_cEnt_
  
> [out] Number of changes to the folder.
    
_pupmovHead_
  
> [out] Chain of [UPMOV](upmov.md) structures. 
    
_pReserved_
  
> [out] This member is reserved for the internal use of Outlook and is not supported.
    
## See also

- [About the Replication API](about-the-replication-api.md)
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)
- [UPTBLE](uptble.md)

