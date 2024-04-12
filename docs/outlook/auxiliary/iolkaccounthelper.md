---
title: "IOlkAccountHelper"
manager: lindalu
ms.date: 12/07/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: fc2972da-80e9-50e2-10b3-585eb63e9103
---

# IOlkAccountHelper

Provides helper functionality in the current MAPI session to manage accounts.
  
## Quick info

|Property|Value|
|:-----|:-----|
|Inherits from:  <br/> |[IUnknown](https://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx) <br/> |
|Provided by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IOlkAccountHelper  <br/> |
   
## Vtable order

|Member|Description|
|:-----|:-----|
|[Placeholder1](iolkaccounthelper-placeholder1.md) <br/> | *This member is a placeholder and is not supported.*  <br/> |
|[GetIdentity](iolkaccounthelper-getidentity.md) <br/> |Gets the profile name of an account. |
|[GetMapiSession](iolkaccounthelper-getmapisession.md) <br/> |Opens a MAPI session and maintains a reference to the session for the account manager. |
|[HandsOffSession](iolkaccounthelper-handsoffsession.md) <br/> |Releases the MAPI session object that was returned by [IOlkAccountHelper::GetMapiSession](iolkaccounthelper-getmapisession.md). |
   
## Remarks

This interface is passed to [IOlkAccountManager::Init](iolkaccountmanager-init.md) when initializing the account manager. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md) 
- [Constants (Account management API)](constants-account-management-api.md)

