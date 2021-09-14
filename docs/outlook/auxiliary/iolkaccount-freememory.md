---
title: "IOlkAccountFreeMemory"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 3b2ee5aa-7639-d86d-447e-50bda54aa3ec
description: "Frees memory allocated by the IOlkAccount interface."
---

# IOlkAccount::FreeMemory

Frees memory allocated by the [IOlkAccount](iolkaccount.md) interface. 
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
```cpp
HRESULT IOlkAccount::FreeMemory (  
    BYTE *pv, 
); 

```

## Parameters

_pv_
  
> [in] A pointer to memory to be freed.
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

Use this method to free memory allocated by [IOlkAccount::GetProp](iolkaccount-getprop.md) (if the value of the specified account property is a binary or string type) and [IOlkAccount::GetAccountInfo](iolkaccount-getaccountinfo.md).
  
## See also

- [IOlkAccount::GetAccountInfo](iolkaccount-getaccountinfo.md)  
- [IOlkAccount::GetProp](iolkaccount-getprop.md)

