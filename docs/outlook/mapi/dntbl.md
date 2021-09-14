---
title: "DNTBL"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 77835b48-43aa-8518-9712-754e84f1e713
description: "Last modified: July 05, 2012"
---

# DNTBL
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for downloading the contents of a folder from the server during the [download table state](download-table-state.md), as part of a full synchronization for contents on a store.
  
## Quick info

```cpp
struct DNTBL 
{ 
    ULONG ulFlags; 
    LPSTREAM pstmReserved1; 
    LPSTREAM pstmReserved2; 
    LPSTREAM pstmReserved3; 
    LPSTREAM pstmReserved4; 
    PXICC pxicc; 
    PXIHC pxihc; 
    LPSTR pszName; 
    FILETIME ftLastMod; 
    ULONG ulRights; 
    FEID feid; 
    UINT uintReserved; 
    DNTBLE rgte[2]; 
    LPSRestriction psrReserved; 
    BOOL boReserved; 
    void* pReserved1; 
    void* pReserved2; 
};

```

## Members

_ulFlags_
  
> [in] Flags to modify behavior 
    
  - DNT_OK
    
    - [in] Download was successful. The client sets this after downloading information from the server.
    
_pstmReserved1_
  
> [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pstmReserved2_
  
> [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pstmReserved3_
  
> [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pstmReserved4_
  
> [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_pxicc_
  
>  [out] Pointer to the **IExchangeImportContentsChanges** contents interface that supports downloading content changes. For more information on **IExchangeImportContentsChanges**, see [ICS Evaluation Criteria](https://msdn.microsoft.com/library/aa579252%28EXCHG.80%29.aspx).
    
_pxihc_
  
>  [out] Pointer to the **IExchangeImportHierarchyChanges** hierarchy interface that supports downloading incremental hierarchy changes. For more information on **IExchangeImportHierarchyChanges**, see [ICS Evaluation Criteria](https://msdn.microsoft.com/library/aa579252%28EXCHG.80%29.aspx).
    
_pszName_
  
>  [out] Name of the folder. 
    
_ftLastMod_
  
>  [out] Last modification time of the folder. 
    
_ulRights_
  
>  [out] Value of the **[PR_RIGHTS](https://msdn.microsoft.com/library/ee238052%28v=EXCHG.80%29.aspx)** property of the folder. 
    
_feid_
  
>  [out] Entry ID of the folder. 
    
_uintReserved_
  
>  [out] This member is reserved for the internal use of Outlook and is not supported. 
    
_rgte_
  
> [out] Changes for normal (or non-hidden) and associated (or hidden) items.  *rgte[0]*  is for normal items, and  *rgte[1]*  is for associated items. Outlook populates this member during the downloading when using Incremental Change Synchronization (ICS). For more information on ICS, see [ICS Evaluation Criteria](https://msdn.microsoft.com/library/aa579252%28EXCHG.80%29.aspx).
    
_lpsrReserved_
  
>  [in]/[out] This member is reserved for the internal use of Outlook and is not supported. 
    
_boReserved_
  
>  [in]This member is reserved for the internal use of Outlook and is not supported. 
    
_pReserved1_
  
>  [out]This member is reserved for the internal use of Outlook and is not supported. 
    
_pReserved2_
  
>  [in]This member is reserved for the internal use of Outlook and is not supported. 
    
## See also

- [About the Replication State Machine](about-the-replication-state-machine.md)  
- [MAPI Constants](mapi-constants.md) 
- [DNTBLE](dntble.md)

