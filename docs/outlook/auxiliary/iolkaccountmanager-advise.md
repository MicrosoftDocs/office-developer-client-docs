---
title: "IOlkAccountManagerAdvise"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c88f087e-4ff4-0837-186d-b6e761468a4d
description: "Registers a client with the account manager for notifications regarding all accounts."
---

# IOlkAccountManager::Advise

Registers a client with the account manager for notifications regarding all accounts.
  
## Quick Info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```
HRESULT IOlkAccountManager::Advise (  
    IOlkAccountNotify *pNotify, 
    DWORD *pdwCookie 
);
```

## Parameters

 _pNotify_
  
> [in] An [IOlkAccountNotify](iolkaccountnotify.md) interface that the account manager will use to send notifications to the client. 
    
 _pdwCookie_
  
> [out] A cookie that [IOlkAccountManager::Unadvise](iolkaccountmanager-unadvise.md) will use when removing the registration for the account. 
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|E_INVALIDARG  <br/> |An invalid argument has been provided.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
   
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccountManager::Unadvise](iolkaccountmanager-unadvise.md)

