---
title: "IOlkAccountManagerSaveChanges"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 32a5d4b7-ead7-24e7-58f2-750232263a0d
description: "Saves changes to the specified account."
---

# IOlkAccountManager::SaveChanges

Saves changes to the specified account.
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT IOlkAccountManager::SaveChanges (  
    DWORD dwAcctID, 
    DWORD dwFlags 
); 
```

## Parameters

_dwAcctID_
  
> [in] The account ID to save. 
    
_dwFlags_
  
> [in] Flags to modify behavior. OLK_ACCOUNT_NO_FLAGS is the only supported value.
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded  <br/> |
|E_ACCT_NOT_FOUND  <br/> |The specified account cannot be found.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## Remarks

After changing the value of account properties by using [IOlkAccount::SetProp](iolkaccount-setprop.md), use **IOlkAccountManager::SaveChanges** or [IOlkAccount::SaveChanges](iolkaccount-savechanges.md) to save such changes. 
  
## See also

- [Constants (Account management API)](constants-account-management-api.md) 
- [IOlkAccount::SaveChanges](iolkaccount-savechanges.md)

