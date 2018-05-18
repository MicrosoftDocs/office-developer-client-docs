---
title: "IOlkAccountSaveChanges"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 8f1ab61e-7d1c-50d5-ae21-8cb4b08d729c
description: "Commits changes to the account object by writing to the registry store."
---

# IOlkAccount::SaveChanges

Commits changes to the account object by writing to the registry store.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
```
HRESULT IOlkAccount::SaveChanges (  
    DWORD dwFlags 
); 
```

## Parameters

 _dwFlags_
  
> [in] Flags to modify behavior. OLK_ACCOUNT_NO_FLAGS is the only supported value.
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The method was successful.  <br/> |
|E_ACCT_NOT_FOUND  <br/> |Cannot find the specified account.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## Remarks

After changing the value of account properties by using [IOlkAccount::SetProp](iolkaccount-setprop.md), use **IOlkAccount::SaveChanges** to save such changes. 
  
## See also



[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccountManager::SaveChanges](iolkaccountmanager-savechanges.md)

