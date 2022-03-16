---
title: "IOlkEnum"
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 33cb89cb-c967-760c-6bc4-94118a4f872c
---

# IOlkEnum

Supports enumerating accounts as [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown.md) objects. 
  
## Quick info

|Key |Value |
|:-----|:-----|
|Inherits from:  |[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown.md) |
|Implemented by: |Outlook  |
|Provided by:    |[IOlkAccountManager::EnumerateAccounts](iolkaccountmanager-enumerateaccounts.md)  |
|Called by:      |Client  |
|Interface identifier: |IID_IOlkEnum  |
   
## Vtable order

|Member |Value |
|:-----|:-----|
|[GetCount](iolkenum-getcount.md) |Gets the number of accounts in the enumerator. |
|[Reset](iolkenum-reset.md)  |Resets the enumerator to the beginning. |
|[GetNext](iolkenum-getnext.md) |Gets the next account in the enumerator. |
|[Skip](iolkenum-skip.md) |Skips a specified number of accounts in the enumerator. |
   
## Remarks

This interface is returned by **IOlkAccountManager::EnumerateAccounts** when obtaining an enumerator of accounts. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md) 
- [Constants (Account management API)](constants-account-management-api.md)
