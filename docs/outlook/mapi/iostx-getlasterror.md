---
title: "IOSTXGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IOSTX.GetLastError
api_type:
- COM
ms.assetid: b25c9288-b391-6303-3643-5a5b66b75c48
---

# IOSTX::GetLastError

  
  
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



[IOSTX::InitSync](iostx-initsync.md)
  
[IOSTX::SetSyncResult](iostx-setsyncresult.md)
  
[IOSTX::SyncBeg](iostx-syncbeg.md)
  
[IOSTX::SyncEnd](iostx-syncend.md)
  
[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)
  
[IOSTX::SyncHdrEnd](iostx-synchdrend.md)
  
[IOSTX : IUnknown](iostxiunknown.md)


[MAPI Constants](mapi-constants.md)

