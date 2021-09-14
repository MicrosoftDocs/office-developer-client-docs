---
title: "IOlkAccountManagerSetOrder"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: e219adf6-e591-72e6-b9bd-2fc62eb5142d
description: "Modifies the ordering of the specified category of accounts."
---

# IOlkAccountManager::SetOrder

Modifies the ordering of the specified category of accounts.
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT SetOrder(
    const CLSID * pclsidCategory,
    DWORD cAccts,
    DWORD rgAccts[]
);

```

## Parameters

_pclsidCategory_
  
> [in] The category class ID for which to set the order. The value must be one of the following:
    
   - CLSID_OlkAddressBook
    
   - CLSID_OlkStore
    
_cAccts_
  
> [in] The number of accounts.
    
_rgAccts_
  
> [in] An array of account IDs. The size of the array is  _cAccts_.
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_ACCT_WRONG_SORT_ORDER  <br/> |The new sort order has a different number of accounts than the old sort order.  <br/> |
|E_INVALIDARG  <br/> |One or more arguments are invalid.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## Remarks

The caller allocates memory for the array pointer  _prgAccts_ as well as for the array at which  _prgAccts_ points. 
  
## See also

- [Constants (Account management API)](constants-account-management-api.md)  
- [IOlkAccountManager::GetOrder](iolkaccountmanager-getorder.md)

