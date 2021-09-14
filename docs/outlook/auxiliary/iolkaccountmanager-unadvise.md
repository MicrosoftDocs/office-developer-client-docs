---
title: "IOlkAccountManagerUnadvise"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: ea5cbf9f-25cc-9cca-9be0-d2deed576153
description: "Unregisters a client with the account manager for notifications for all accounts."
---

# IOlkAccountManager::Unadvise

Unregisters a client with the account manager for notifications for all accounts. 
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT Unadvise(
    DWORD dwCookie
);

```

## Parameters

_dwCookie_
  
> [in] The cookie returned by [IOlkAccountManager::Advise](iolkaccountmanager-advise.md).
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_INVALIDARG  <br/> |One or more arguments are invalid.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## See also

- [Constants (Account management API)](constants-account-management-api.md)  
- [IOlkAccountManager::Advise](iolkaccountmanager-advise.md)

