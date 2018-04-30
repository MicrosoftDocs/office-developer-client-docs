---
title: "IOlkAccountNotify"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 360854bb-e9be-a784-e80b-3f18418ded1b

---

# IOlkAccountNotify

Provides a callback to the client for changes to an account.
  
## Quick Info

|||
|:-----|:-----|
|Inherits from:  <br/> |[IOlkErrorUnknown](iolkerrorunknown.md) <br/> |
|Provided by:  <br/> | Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkAccountNotify  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[Notify](iolkaccountnotify-notify.md) <br/> |Notifies the client of changes to the specified account.  <br/> |
   
## Remarks

This interface is passed to [IOlkAccountManager::Advise](iolkaccountmanager-advise.md) when setting up notifications. 
  
## See also

#### Concepts

[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)

