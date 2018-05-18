---
title: "PROP_ACCT_ID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: b72124aa-2e85-057c-9343-a40af60b91a0
description: "Returns an identifier that uniquely identifies an account within the profile in which the account is created."
---

# PROP_ACCT_ID

Returns an identifier that uniquely identifies an account within the profile in which the account is created.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x0001  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Property tag:  <br/> |0x00010003  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md). If the client attempts to set this property, this property returns **E_OLK_PROP_READ_ONLY**. 
  
This property is different from [PROP_ACCT_MINI_UID](prop_acct_mini_uid.md) in that its value is unique only among all the accounts within that profile in which the account was created, whereas **PROP_ACCT_MINI_UID** uniquely identifies the account within and outside of the profile in which the account was created. When a message with these properties roams onto a second computer with a different Outlook profile and different set of accounts, **PROP_ACCT_ID** can possibly conflict with an account in the profile of the second computer, and **PROP_ACCT_MINI_UID** can uniquely identify the original account in the original profile. 
  
## See also



[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)

