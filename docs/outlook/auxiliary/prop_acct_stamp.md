---
title: "PROP_ACCT_STAMP"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 70b6ecc8-6be3-0f05-3291-ac5b7f2ecfdb
description: "Returns the account stamp."
---

# PROP_ACCT_STAMP

Returns the account stamp.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x000D  <br/> |
|Property type:  <br/> |PT_UNICODE  <br/> |
|Property tag:  <br/> |0x000D001F  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md). If the client attempts to set this property, this property returns **E_OLK_PROP_READ_ONLY**. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md)  
- [Constants (Account management API)](constants-account-management-api.md)

