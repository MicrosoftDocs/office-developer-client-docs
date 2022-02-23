---
title: "IOlkAccountGetAccountInfo"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 97f08cde-d6e4-8935-1758-4018a3baf682
description: "Gets the type and categories information for the specified account."
---

# IOlkAccount::GetAccountInfo

Gets the type and categories information for the specified account.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
```cpp
HRESULT IOlkAccount::GetAccountInfo(  
    CLSID *pclsidType, 
    DWORD *pcCategories, 
    CLSID **prgclsidCategory 
);

```

## Parameters

_pclsidType_
  
> [out] The class identifier for the account type. The value must be one of the following:

- CLSID_OlkPOP3Account

- CLSID_OlkIMAP4Account

- CLSID_OlkMAPIAccount

- CLSID_OlkHotmailAccount

- CLSID_OlkLDAPAccount

_pcCategories_
  
> [out] The number of categories in  _prgclsidCategory_.

_prgclsidCategory_
  
> [out] An array of categories that this account is associated with. The array is of size * _pcCategories_. The value of each category in the array must be one of the following:

- CLSID_OlkMail

- CLSID_OlkAddressBook

- CLSID_OlkStore

## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

After this method returns, you must free _prgclsidCategory_ by using [IOlkAccount::FreeMemory](iolkaccount-freememory.md).
  
**IOlkAccount::GetAccountInfo** does not support the address book category for an Exchange account. If the account is an Exchange account (_pclsidType_ is **CLSID_OlkMAPIAccount** ), and the account implements the address book, calling **IOlkAccount::GetAccountInfo** will not return **CLSID_OlkAddressBook** as a category in _prgclsidCategory_.
  
## See also

- [Constants (Account management API)](constants-account-management-api.md)  
- [IOlkAccount::FreeMemory](iolkaccount-freememory.md)
