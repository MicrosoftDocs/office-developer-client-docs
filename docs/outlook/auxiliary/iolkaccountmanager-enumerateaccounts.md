---
title: "IOlkAccountManagerEnumerateAccounts"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: dbb8342b-e4e0-f89d-3e14-b4c7049095ef
description: "Gets an enumerator for the accounts of the specific category or type."
---

# IOlkAccountManager::EnumerateAccounts

Gets an enumerator for the accounts of the specific category or type.
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```
HRESULT IOlkAccountManager::EnumerateAccounts (  
    const CLSID *pclsidCategory, 
    const CLSID *pclsidType, 
    DWORD dwFlags, 
    IOlkEnum **ppEnum 
);

```

## Parameters

 _pclsidCategory_
  
> [in] The class identifier of the category to enumerate. The value must be one of the following:
    
    - CLSID_OlkMail 
    
    -  CLSID_OlkAddressBook 
    
    - CLSID_OlkStore 
    
 _pclsidType_
  
> [in] The class identifier of the account type to enumerate. The value must be one of the following:
    
    - CLSID_OlkPOP3Account
    
    - CLSID_OlkIMAP4Account
    
    - CLSID_OlkMAPIAccount
    
    - CLSID_OlkHotmailAccount
    
    - CLSID_OlkLDAPAccount
    
 _dwFlags_
  
> [in] Flags to modify behavior. The only supported value is OLK_ACCOUNT_NO_FLAGS.
    
 _ppEnum_
  
> [out] An enumerator that supports the [IOlkEnum](iolkenum.md) interface. 
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## Remarks

Specifying NULL for category returns an enumerator of all accounts of the specified type. Similarly, specifying NULL for type returns an enumerator of all accounts of the specified category.
  
 **IOlkAccountManager::EnumerateAccounts** does not support the address book category for an Exchange account. If the account is an Exchange account (*pclsidType*  is **CLSID_OlkMAPIAccount** ), and you are trying to enumerate accounts that implement the address book (*prgclsidCategory*  is **CLSID_OlkAddressBook** ), calling **IOlkAccountManager::EnumerateAccounts** will not return the Exchange account in the accounts enumerator  *ppEnum*  . 
  
## See also



[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkEnum](iolkenum.md)

