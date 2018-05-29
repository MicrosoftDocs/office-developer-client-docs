---
title: "PROP_ACCT_DELIVERY_FOLDER"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: a409c49b-b390-021e-2ec1-7a5932a0c8de
description: "Represents the Entry ID of the default delivery folder for the account."
---

# PROP_ACCT_DELIVERY_FOLDER

Represents the Entry ID of the default delivery folder for the account.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x0019  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x00190102  <br/> |
|Access:  <br/> |Read/write  <br/> |
   
## Remarks

Get or set this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md) or [IOlkAccount::SetProp](iolkaccount-setprop.md), respectively.
  
The default delivery folder is **Inbox**.
  
## See also

- [About the Account Management API](about-the-account-management-api.md)  
- [Constants (Account management API)](constants-account-management-api.md)

