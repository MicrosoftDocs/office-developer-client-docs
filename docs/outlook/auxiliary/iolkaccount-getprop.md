---
title: "IOlkAccountGetProp"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 5725eb52-3a78-897d-f9e3-c5a494fb78c0
description: "Gets the value of the specified account property."
---

# IOlkAccount::GetProp

Gets the value of the specified account property.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
```cpp
HRESULT IOlkAccount::GetProp(  
DWORD dwProp, 
ACCT_VARIANT *pVar 
);
```

## Parameters

_dwProp_
  
> [in] The property tag of the account property to get.
    
_pVar_
  
> [out] The value of the specified property.
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded. |
|E_ACCT_NOT_FOUND  <br/> |The property is not found for the given account. |
|E_INVALIDARG  <br/> |An invalid property tag has been specified. |
   
## Remarks

After this method returns, if the value of the account property is a binary or string type, you must free  *pVar*  by using [IOlkAccount::FreeMemory](iolkaccount-freememory.md).
  
## See also

- [Constants (Account management API)](constants-account-management-api.md) 
- [IOlkAccount::FreeMemory](iolkaccount-freememory.md)  
- [IOlkAccount::SetProp](iolkaccount-setprop.md)

