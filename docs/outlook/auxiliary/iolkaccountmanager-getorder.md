---
title: "IOlkAccountManagerGetOrder"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: bd22026c-e4f7-2f25-0ef2-5d9539fd7eee
description: "Gets the ordering of the specified category of accounts."
---

# IOlkAccountManager::GetOrder

Gets the ordering of the specified category of accounts.
  
## Quick Info

See [IOlkAccountManager](iolkaccountmanager.md)
  
```
HRESULT IOlkAccountManager::GetOrder (  
    const CLSID *pclsidCategory, 
    DWORD *pcAccts, 
    DWORD *prgAccts[] 
); 
```

## Parameters

 _pclsidCategory_
  
> [in] The category class ID for which to get the order. The value must be one of the following:
    
    - CLSID_OlkMail
    
    - CLSID_OlkAddressBook
    
    - CLSID_OlkStore
    
 _pcAccts_
  
>  [out] The number of accounts. 
    
 _prgAccts_
  
> [out] A pointer to an array of accounts.
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded  <br/> |
|E_INVALIDARG  <br/> |One or more arguments are invalid.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## Remarks

Before calling this method, the caller allocates only an array pointer  *prgAccts*  but no memory for the array at which  *prgAccts*  points. After this method returns, the caller must use [IOlkAccountManager::FreeMemory](iolkaccountmanager-freememory.md) to release the memory allocated for  *prgAccts*  . 
  
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccountManager::SetOrder](iolkaccountmanager-setorder.md)

