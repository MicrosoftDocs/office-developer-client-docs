---
title: "IOlkAccountManagerUnadvise"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ea5cbf9f-25cc-9cca-9be0-d2deed576153
description: "Unregisters a client with the account manager for notifications for all accounts."
---

# IOlkAccountManager::Unadvise

Unregisters a client with the account manager for notifications for all accounts. 
  
## Quick Info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```
HRESULT Unadvise(
    DWORD dwCookie
);

```

## Parameters

 _dwCookie_
  
> [in] The cookie returned by [IOlkAccountManager::Advise](iolkaccountmanager-advise.md).
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_INVALIDARG  <br/> |One or more arguments are invalid.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccountManager::Advise](iolkaccountmanager-advise.md)

