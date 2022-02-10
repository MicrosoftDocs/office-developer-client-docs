---
title: "IOlkAccountManagerFindAccount"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference 
ms.localizationpriority: medium
ms.assetid: 31004aec-7bd2-6e12-83eb-1a32da121c54
description: "Finds an account by property value."
---

# IOlkAccountManager::FindAccount

Finds an account by property value.
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT IOlkAccountManager::FindAccount (  
    DWORD dwProp, 
    ACCT_VARIANT *pVar, 
    IOlkAccount **ppAccount 
);
```

## Parameters

_dwProp_
  
> [in] The property to search on. Must be [PROP_ACCT_ID](prop_acct_id.md) or [PROP_ACCT_IS_EXCH](prop_acct_is_exch.md).
    
_pVar_
  
> [in] The value to match.
    
_ppAccount_
  
> [out] The account found. This object supports an [IOlkAccount](iolkaccount.md) interface. 
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded. |
|E_ACCT_NOT_FOUND  <br/> |The specified account cannot be found. |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use. |
|E_OLK_PARAM_NOT_SUPPORTED  <br/> |One or more parameters are invalid. |
   
## See also

- [ACCT_VARIANT](acct_variant.md)  
- [Constants (Account management API)](constants-account-management-api.md)  
- [IOlkAccountHelper](iolkaccounthelper.md)

