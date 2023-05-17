---
title: "IPSTXGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IPSTX.GetLastError
api_type:
- COM
ms.assetid: 68dc0ecc-881e-de69-faaa-90acb9857031
---

# IPSTX::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Gets extended information about the last error.
  
```cpp
HRESULT GetLastError( 
    HRESULT hResult, 
    ULONG ulFlags, 
    LPMAPIERROR *lppMAPIError 
);
```

## Parameters

 _hResult_
  
> [in] Error code. 
    
 _ulFlags_
  
> [in] Flags to modify behavior. This must be 0. 
    
 _lppMAPIError_
  
> [out] Pointer to the **MAPIERROR** structure that contains the extended information for the error. See mapidefs.h for the type definition of **LPMAPIERROR**. 
    
## See also



[IPSTX::EmulateSpooler](ipstx-emulatespooler.md)
  
[IPSTX::GetSyncObject](ipstx-getsyncobject.md)

