---
title: "PROP_ACCT_IS_EXCH"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 599bfc7d-7b62-7cc1-69ff-6db04c96a49b
description: "True if the account is an Exchange account."
---

# PROP_ACCT_IS_EXCH

True if the account is an Exchange account.
  
## Quick Info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x0014  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Property tag:  <br/> |0x00140003  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md). If the client attempts to set this property, this property returns **E_OLK_PROP_READ_ONLY**. 
  
## See also

#### Concepts

[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)

