---
title: "IOlkAccountNotify"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference 
ms.localizationpriority: medium
ms.assetid: 360854bb-e9be-a784-e80b-3f18418ded1b
---

# IOlkAccountNotify

Provides a callback to the client for changes to an account.
  
## Quick info

|||
|:-----|:-----|
|Inherits from:  <br/> |[IOlkErrorUnknown](iolkerrorunknown.md) <br/> |
|Provided by:  <br/> | Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkAccountNotify  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[Notify](iolkaccountnotify-notify.md) <br/> |Notifies the client of changes to the specified account.  <br/> |
   
## Remarks

This interface is passed to [IOlkAccountManager::Advise](iolkaccountmanager-advise.md) when setting up notifications. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md) 
- [Constants (Account management API)](constants-account-management-api.md)

