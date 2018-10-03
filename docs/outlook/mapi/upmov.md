---
title: "UPMOV"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 098743a5-f265-639a-8ba6-1412705bee0a
description: "Last modified: July 05, 2012"
---

# UPMOV
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for uploading items that have been moved. This information is used during the [upload delete status state](upload-delete-status-state.md) and [upload table state](upload-table-state.md).
  
## Quick info

```cpp
struct UPMOV 
{ 
      ULONG          ulFlags; 
      LPVOID         pReserved; 
      LPSTREAM       pstmReserved; 
      LPSTR          pszName; 
      FEID           feid; 
      LPMAPIFOLDER   pfld; 
      PXICC          pxicc; 
      DWORD          dwReserved; 
      PUPMOV         pupmovNext; 
      UINT           cEntMov; 
};
```

## Members

_ulFlags_
  
> [in] Flags to determine the appropriate behavior during the upload.
    
  - UPV_ERROR
    
    - [in] Problem opening server folder.
    
  - UPV_DIRTY
    
    - [in] The upload state has changed. This is used by the client to track the change in state for the local store.
    
  - UPV_COMMIT
    
    - [in] Commit upload state.
    
_pReserved_
  
>  [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pstmReserved_
  
>  [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pszName_
  
>  [out] Name of the destination folder. 
    
  > [!NOTE]
  > This member does not support UNICODE. 
  
_feid_
  
>  [out] Entry ID of destination folder. 
    
_pfld_
  
>  [in] Pointer to server folder. 
    
_pxicc_
  
>  [in] Pointer to the **IExchangeImportContentsChanges** contents interface that supports uploading content changes when using Incremental Change Synchronization (ICS). For more information on **IExchangeImportContentsChanges** and ICS, see [ICS Evaluation Criteria](https://msdn.microsoft.com/library/aa579252%28EXCHG.80%29.aspx).
    
_dwReserved_
  
>  [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pupmovNext_
  
>  [out] Next move context. 
    
_cEntMov_
  
>  [in] Number of items moved here. 
    
## See also

- [About the Replication API](about-the-replication-api.md)
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)
- [FEID](feid.md)

