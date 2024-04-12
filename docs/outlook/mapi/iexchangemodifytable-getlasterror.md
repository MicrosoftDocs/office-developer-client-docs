---
title: "IExchangeModifyTableGetLastError"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IExchangeModifyTable.GetLastError
api_type:
- COM
ms.assetid: b850dc08-73c3-4b19-ae29-1892d6a2ff2f
---

# IExchangeModifyTable::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns information about the last error that occurred in a table object.
  
```cpp
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



[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)
  
[MAPIERROR](mapierror.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

