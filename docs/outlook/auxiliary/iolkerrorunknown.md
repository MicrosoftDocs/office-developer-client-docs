---
title: "IOlkErrorUnknown"
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 9cfbf12c-a71c-092b-d86a-c5585b0f1edb
---

# IOlkErrorUnknown

Provides extra information about the last error.
  
## Quick info

|Property |Value |
|:-----|:-----|
|Inherits from:   |[IUnknown](/cpp/atl/iunknown) |
|Provided by:   |Client  |
|Interface identifier:   |IID_IOlkErrorUnknown  |
   
## Vtable order

|Member | Description |
|:-----|:-----|
|[GetLastError](iolkerrorunknown-getlasterror.md) <br/> |Gets a message string for the specified error. |
   
## Remarks

This interface provides extra information about an error in [IOlkAccountManager](iolkaccountmanager.md), [IOlkAccountNotify](iolkaccountnotify.md), and [IOlkAccount](iolkaccount.md). It is also the base interface for **IOlkAccountManager**, **IOlkAccountNotify**, and **IOlkAccount**. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md)
