---
title: "IOlkAccountHelper"
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: fc2972da-80e9-50e2-10b3-585eb63e9103
 
 
---

# IOlkAccountHelper

Provides helper functionality in the current MAPI session to manage accounts.
  
## Quick Info

|||
|:-----|:-----|
|Inherits from:  <br/> |[IUnknown](http://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx) <br/> |
|Provided by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkAccountHelper  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[Placeholder1](iolkaccounthelper-placeholder1.md) <br/> | *This member is a placeholder and is not supported.*  <br/> |
|[GetIdentity](iolkaccounthelper-getidentity.md) <br/> |Gets the profile name of an account.  <br/> |
|[GetMapiSession](iolkaccounthelper-getmapisession.md) <br/> |Opens a MAPI session and maintains a reference to the session for the account manager.  <br/> |
|[HandsOffSession](iolkaccounthelper-handsoffsession.md) <br/> |Releases the MAPI session object that was returned by [IOlkAccountHelper::GetMapiSession](iolkaccounthelper-getmapisession.md).  <br/> |
   
## Remarks

This interface is passed to [IOlkAccountManager::Init](iolkaccountmanager-init.md) when initializing the account manager. 
  
## See also

#### Concepts

[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)

