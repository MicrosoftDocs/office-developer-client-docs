---
title: "IPSTXGetSyncObject"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPSTX.GetSyncObject
api_type:
- COM
ms.assetid: b93dae79-4305-9a3a-7b93-42319f7e26ba
description: "Last modified: July 23, 2011"
---

# IPSTX::GetSyncObject

  
  
**Applies to**: Outlook 
  
Starts a synchronization session and gets the associated **[IOSTX](iostxiunknown.md)** interface. 
  
```
HRESULT GetSyncObject( 
   IOSTX **ppostx 
);
```

## Parameters

 _ppostx_
  
>  [out] Pointer to the **IOSTX** interface to get. 
    
## Remarks

The caller must ensure that the same folder is not synchronized at the same time on more than one thread.
  
## See also

#### Reference

[IPSTX::EmulateSpooler](ipstx-emulatespooler.md)
  
[IPSTX::GetLastError](ipstx-getlasterror.md)

