---
title: "IOlkAccountManager"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 544c87e5-887d-82ec-bf1a-0d95027fe0ec
---

# IOlkAccountManager

Manages access to accounts and sets up notifications about account changes.
  
## Quick info

|||
|:-----|:-----|
|Inherits from:  <br/> |[IOlkErrorUnknown](iolkerrorunknown.md) <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
|Provided by:  <br/> |CLSID_OlkAccountManager  <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkAccountManager  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[Init](iolkaccountmanager-init.md) <br/> |Initializes the account manager for use.  <br/> |
|[DisplayAccountList](iolkaccountmanager-displayaccountlist.md) <br/> |Displays either the **Account Settings** or **Add New Account** dialog box.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
|[FindAccount](iolkaccountmanager-findaccount.md) <br/> |Finds an account by property value.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
|[DeleteAccount](iolkaccountmanager-deleteaccount.md) <br/> |Deletes the specified account.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
|[SaveChanges](iolkaccountmanager-savechanges.md) <br/> |Saves changes to the specified account.  <br/> |
|[GetOrder](iolkaccountmanager-getorder.md) <br/> |Gets the ordering of the specified category of accounts.  <br/> |
|[SetOrder](iolkaccountmanager-setorder.md) <br/> |Modifies the ordering of the specified category of accounts.  <br/> |
|[EnumerateAccounts](iolkaccountmanager-enumerateaccounts.md) <br/> |Gets an enumerator for the accounts of the specific category and type.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
|[FreeMemory](iolkaccountmanager-freememory.md) <br/> |Frees memory allocated by the **IOlkAccountManager** interface.  <br/> |
|[Advise](iolkaccountmanager-advise.md) <br/> |Registers a client with the account manager for notifications regarding all accounts.  <br/> |
|[Unadvise](iolkaccountmanager-unadvise.md) <br/> |Unregisters a client with the account manager for notifications for all accounts.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented*  <br/> |
   
## See also

- [About the Account Management API](about-the-account-management-api.md)

