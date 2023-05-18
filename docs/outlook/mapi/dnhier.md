---
title: "DNHIER"
description: "DNHIER provides information for downloading a hierarchy from the server during the download hierarchy state, which is part of a full hierarchy synchronization."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 3953dc9d-0146-3689-63f0-c6ba78566b8b
---

# DNHIER

**Applies to**: Outlook 2013 | Outlook 2016
  
Information for downloading a hierarchy from the server during the [download hierarchy state](download-hierarchy-state.md), which is part of a full hierarchy synchronization. This downloading process uses Microsoft Exchange Incremental Change Synchronization (ICS). For more information on ICS, see [ICS Evaluation Criteria](https://msdn.microsoft.com/library/aa579252%28EXCHG.80%29.aspx).
  
## Quick info

```cpp
struct DNHIER 
{ 
    ULONG ulFlags; 
    LPSTREAM pstmReserved; 
    PXIHC pxihc; 
    UINT cEntNew; 
   UINT cEntMod; 
    UINT cEntDel; 
};
```

## Members

_ulFlags_
  
> [in] Flags to determine the appropriate behavior during the download.

- DNH_OK

- [in] Download was successful. The client sets this after downloading information from the server.

_pstmReserved_
  
> [out] This member is reserved for the internal use of Outlook and is not supported.

_pxihc_
  
> [out] Pointer to the **IExchangeImportHierarchyChanges** hierarchy interface that supports downloading incremental hierarchy changes. For more information on **IExchangeImportHierarchyChanges**, see [ICS Evaluation Criteria](https://msdn.microsoft.com/library/aa579252%28EXCHG.80%29.aspx).

_cEntNew_
  
> [out] Number of folders added to the local store. Outlook populates this value during the downloading when using ICS.

_cEntMod_
  
> [out] Number of folders to be modified on the local store. Outlook populates this value during the downloading when using ICS.

_cEntDel_
  
> [out] Number of folders to be deleted on the local store. Outlook populates this value during the downloading when using ICS.

## See also

- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)
