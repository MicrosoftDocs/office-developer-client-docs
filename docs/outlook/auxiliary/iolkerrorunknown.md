---
title: "IOlkErrorUnknown"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 9cfbf12c-a71c-092b-d86a-c5585b0f1edb
---

# IOlkErrorUnknown

Provides extra information about the last error.
  
## Quick info

|||
|:-----|:-----|
|Inherits from:  <br/> |[IUnknown](https://docs.microsoft.com/en-us/windows/desktop/api/unknwn/nn-unknwn-iunknown) <br/> |
|Provided by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkErrorUnknown  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](iolkerrorunknown-getlasterror.md) <br/> |Gets a message string for the specified error.  <br/> |
   
## Remarks

This interface provides extra information about an error in [IOlkAccountManager](iolkaccountmanager.md), [IOlkAccountNotify](iolkaccountnotify.md), and [IOlkAccount](iolkaccount.md). It is also the base interface for **IOlkAccountManager**, **IOlkAccountNotify**, and **IOlkAccount**. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md)

