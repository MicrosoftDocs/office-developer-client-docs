---
title: "PROP_ACCT_MINI_UID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 30d8268e-0c64-401d-8799-e8e1ba78b88f
description: "Returns an account identifier that is unique across Outlook profiles."
---

# PROP_ACCT_MINI_UID

Returns an account identifier that is unique across Outlook profiles.
  
## Quick Info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x0003  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Property tag:  <br/> |0x00030003  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md). If the client attempts to set this property, this property returns **E_OLK_PROP_READ_ONLY**. 
  
This property is different from [PROP_ACCT_ID](prop_acct_id.md) in that its value uniquely identifies the account within and outside of the profile in which the account was created, whereas **PROP_ACCT_ID** is unique only among all the accounts within that one profile in which the account was created. When a message with these properties roams onto a second computer with a different Outlook profile and different set of accounts, **PROP_ACCT_MINI_UID** can uniquely identify the original account in the original profile. However, **PROP_ACCT_ID** can possibly conflict with an account in the profile of the second computer. 
  
## See also

#### Concepts

[PROP_ACCT_ID](prop_acct_id.md)
  
[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)

