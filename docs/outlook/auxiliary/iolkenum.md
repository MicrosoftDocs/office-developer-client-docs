---
title: "IOlkEnum"
manager: soliver
ms.date: 12/08/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 33cb89cb-c967-760c-6bc4-94118a4f872c
---

# IOlkEnum

Supports enumerating accounts as [IUnknown](https://docs.microsoft.com/en-us/windows/desktop/api/unknwn/nn-unknwn-iunknown) objects. 
  
## Quick info

|||
|:-----|:-----|
|Inherits from:  <br/> |[IUnknown](https://docs.microsoft.com/en-us/windows/desktop/api/unknwn/nn-unknwn-iunknown) <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
|Provided by:  <br/> |[IOlkAccountManager::EnumerateAccounts](iolkaccountmanager-enumerateaccounts.md) <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkEnum  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetCount](iolkenum-getcount.md) <br/> |Gets the number of accounts in the enumerator.  <br/> |
|[Reset](iolkenum-reset.md) <br/> |Resets the enumerator to the beginning.  <br/> |
|[GetNext](iolkenum-getnext.md) <br/> |Gets the next account in the enumerator.  <br/> |
|[Skip](iolkenum-skip.md) <br/> |Skips a specified number of accounts in the enumerator.  <br/> |
   
## Remarks

This interface is returned by **IOlkAccountManager::EnumerateAccounts** when obtaining an enumerator of accounts. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md) 
- [Constants (Account management API)](constants-account-management-api.md)

