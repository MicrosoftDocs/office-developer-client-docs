---
title: "PROP_ACCT_DELIVERY_STORE"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: f5db43e9-687b-d467-1be1-3737e3f91c27
description: "Represents the Entry ID of the default delivery store for the account."
---

# PROP_ACCT_DELIVERY_STORE

Represents the Entry ID of the default delivery store for the account.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|Property |Value |
|:-----|:-----|
|Identifier:  <br/> |0x0018  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x00180102  <br/> |
|Access:  <br/> |Read/write  <br/> |
   
## Remarks

Get or set this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md) or [IOlkAccount::SetProp](iolkaccount-setprop.md), respectively.
  
One of the side effects of setting a store as the default delivery store for an account is that when starting Outlook, Outlook creates search folders for that store if they do not already exist, and list the store in the To-Do Bar.
  
## See also

- [About the Account Management API](about-the-account-management-api.md)
- [Constants (Account management API)](constants-account-management-api.md)

