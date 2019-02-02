---
title: "IOlkAccountManagerInit"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 0e5ffb61-1469-bc91-f237-27d1156179cd
description: "Initializes the account manager for use."
---

# IOlkAccountManager::Init

Initializes the account manager for use.
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT IOlkAccountManager::Init (  
    IOlkAccountHelper *pAcctHelper, 
    DWORD dwFlags 
);

```

## Parameters

_pAcctHelper_
  
> [in] An [IOlkAccountHelper](iolkaccounthelper.md) interface that provides account helper functionality. 
    
_dwFlags_
  
> [in] Flags to modify behavior.
    
   - **ACCT_INIT_NO_STORES_CHECK** —Prevents an account (such as an IMAP account) from synchronizing with an associated store. 
    
   - **ACCT_INIT_NOSYNCH_MAPI_ACCTS** —Prevents MAPI services from synchronizing with accounts. 
   
   - **ACCT_INIT_NO_NOTIFICATIONS** —Prevents the Account Manager from intercepting broadcast messages intended for other applications. 
   
   - **OLK_ACCOUNT_NO_FLAGS** —Synchronizes MAPI services with accounts. 
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_OLK_ALREADY_INITIALIZED  <br/> |**Init** has already been called.  <br/> |
|E_OLK_REGISTRY  <br/> |The account manager could not access the required registry settings.  <br/> |
   
## Remarks

The client must call **IOlkAccountManager::Init** to initialize the account manager before using the account manager to access accounts or set up notifications. Because Outlook automatically synchronizes MAPI services with accounts on startup, use **ACCT_INIT_NOSYNCH_MAPI_ACCTS** unless there is a specific cause to synchronize. 
  
## See also

- [Constants (Account management API)](constants-account-management-api.md)

