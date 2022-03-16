---
title: "PROP_ACCT_SEND_STAMP"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: b86242f3-dfd7-398e-a054-93db85b69752
description: "Returns the accountsendstamp."
---

# PROP_ACCT_SEND_STAMP

Returns the account "send" stamp.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|Key |Value |
|:-----|:-----|
|Identifier:  <br/> |0x000E  <br/> |
|Property type:  <br/> |PT_UNICODE  <br/> |
|Property tag:  <br/> |0x000E001F  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md). If the client attempts to set this property, this property returns **E_OLK_PROP_READ_ONLY**. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md)  
- [Constants (Account management API)](constants-account-management-api.md)

