---
title: "IExchangeModifyTableGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IExchangeModifyTable.GetLastError
api_type:
- COM
ms.assetid: b850dc08-73c3-4b19-ae29-1892d6a2ff2f
description: "Last modified: July 23, 2011"
---

# IExchangeModifyTable::GetLastError

  
  
**Applies to**: Outlook 
  
Returns information about the last error that occurred in a table object.
  
```
HRESULT GetLastError( 
  HRESULT hResult, 
  ULONG ulFlags, 
  LPMAPIERROR FAR * lppMAPIError 
); 
```

## Parameters

 _hResult_
  
> [in] The return value from the method that failed.
    
 _ulFlags_
  
> [in] Not used, set to 0 (zero).
    
 _lppMAPIError_
  
> [out] Points to a MAPI [MAPIERROR](mapierror.md) structure that contains information about the last error that occurred for a table object. 
    
## See also

#### Reference

[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)
  
[MAPIERROR](mapierror.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

