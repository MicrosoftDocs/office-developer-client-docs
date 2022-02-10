---
title: "IOlkAccountManagerDeleteAccount"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: df210364-fe20-8e33-a455-9902f04ec739
description: "Deletes the specified account."
---

# IOlkAccountManager::DeleteAccount

Deletes the specified account.
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT IOlkAccountManager::DeleteAccount (  
    DWORD dwAcctID, 
);
```

## Parameters

_dwAcctID_
  
> [in] The account ID of the account to be deleted.
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded  <br/> |
|E_ACCT_NOT_FOUND  <br/> |The specified account cannot be found. |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use. |
   
## See also

- [Constants (Account management API)](constants-account-management-api.md)  
- [IOlkAccountManager::FindAccount](iolkaccountmanager-findaccount.md)

