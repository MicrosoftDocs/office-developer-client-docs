---
title: "IOlkErrorUnknownGetLastError"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 3f332de3-470d-9bc2-0c65-684bb58bcd7a
description: "Gets a message string for the specified error."
---

# IOlkErrorUnknown::GetLastError

Gets a message string for the specified error. 
  
## Quick info

See [IOlkErrorUnknown](iolkerrorunknown.md).
  
```cpp
HRESULT IOlkErrorUnknown::GetLastError(  
    HRESULT hr, 
    LPWSTR *ppwszError 
); 

```

## Parameters

_hr_
  
> [in] The error code to look up.
    
_ppwszError_
  
> [out] The error message that corresponds to  *hr*  . 
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_INVALIDARG  <br/> |One or more arguments are invalid.  <br/> |
   
## See also

- [Constants (Account management API)](constants-account-management-api.md)

