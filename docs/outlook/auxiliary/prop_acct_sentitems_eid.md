---
title: "PROP_ACCT_SENTITEMS_EID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: f199a97f-55d6-9297-adc4-e9f7b4b5f58b
description: "Represents the Entry ID of the default folder for sent items for the account."
---

# PROP_ACCT_SENTITEMS_EID

Represents the Entry ID of the default folder for sent items for the account. 
  
## Quick Info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x0020  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x00200102  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md).
  
The default folder for sent items is **Sent Items**.
  
This property is read-only for POP3 and IMAP accounts. Attempting to set this property for these types of accounts returns **E_ACCT_NOT_FOUND**. 
  

