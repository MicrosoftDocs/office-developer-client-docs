---
title: "SYNCCONT"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b4307a3-5a8c-89bf-1113-2549556a7fe7
description: "Last modified: July 23, 2011"
---

# SYNCCONT

**Applies to**: Outlook 
  
Information for synchronizing the contents of specified folders in a local store with the server during the [synchronize contents state](synchronize-contents-state.md). This involves just uploading, or a full synchronization involving an upload and then a download.
  
## Quick Info

```cpp
struct SYNCCONT 
{ 
   ULONG   ulFlags; 
   UINT   iEnt; 
   UINT   cEnt; 
   LPVOID    pvReserved; 
   LPSPropTagArray   ptagaReserved; 
   LPSSortOrderSet   psosReserved; 
};
```

## Members

_ulFlags_
  
> [in] Flags to determine the appropriate behavior during synchronization.
    
  - UPC_OK
    
  - [in] Upload or full synchronization was successful. The client sets this after synchronizing information with the server.
    
_iEnt_
  
> [out] Index to track synchronizing the contents in the number of folders specified by  _cEnt_.
    
_cEnt_
  
> [out] Number of folders to be replicated.
    
_pvReserved_
  
> This member is reserved for the internal use of Outlook and is not supported. 
    
_ptagaReserved_
  
> This member is reserved for the internal use of Outlook and is not supported. 
    
_psosReserved_
  
> This member is reserved for the internal use of Outlook and is not supported. 
    
## See also

- [About the Replication API](about-the-replication-api.md)
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)

