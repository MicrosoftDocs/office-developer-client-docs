---
title: "IOlkAccountManagerFreeMemory"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: acb67186-ab38-e918-5402-2526307a5bd0
description: "Frees memory allocated by the IOlkAccountManager interface."
---

# IOlkAccountManager::FreeMemory

Frees memory allocated by the [IOlkAccountManager](iolkaccountmanager.md) interface. 
  
## Quick Info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```
HRESULT IOlkAccountManager::FreeMemory (  
    BYTE *pv, 
);
```

## Parameters

 _pv_
  
> [in] A pointer to the memory to free.
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

Use this method to release memory allocated by [IOlkAccountManager::GetOrder](iolkaccountmanager-getorder.md).
  
## See also

#### Concepts

[IOlkAccountManager::GetOrder](iolkaccountmanager-getorder.md)

