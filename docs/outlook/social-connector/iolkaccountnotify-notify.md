---
title: "IOlkAccountNotifyNotify"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dbce1c47-1252-ddeb-64ae-d52118e6821f
description: "Notifies the client of changes to the specified account."
---

# IOlkAccountNotify::Notify

Notifies the client of changes to the specified account.
  
## Quick Info

See [IOlkAccountNotify](iolkaccountnotify.md).
  
```
HRESULT IOlkAccount::Notify(  
    DWORD dwNotify, 
    DWORD dwAcctID, 
    DWORD dwFlags 
);

```

## Parameters

 _dwNotify_
  
> [in] The type of notification. The value must be one of the following:
    
    - NOTIFY_ACCT_CHANGED 
    
    - NOTIFY_ACCT_CREATED 
    
    - NOTIFY_ACCT_DELETED
    
    - NOTIFY_ACCT_ORDER_CHANGED 
    
    - NOTIFY_ACCT_PREDELETED 
    
 _dwAcctID_
  
> [in] The account ID of the account that has been created, changed, deleted, or pre-deleted.
    
 _dwFlags_
  
>  [in] Not used. OLK_ACCOUNT_NO_FLAGS is the only supported value. 
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccountManager](iolkaccountmanager.md)

