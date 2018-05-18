---
title: "PROP_MAPI_EMSMDB_UID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 8e5b42e3-844f-488c-ba6f-b74c447b1d59
description: "Represents an ACCT_BIN structure that contains the UID of an Exchange account."
---

# PROP_MAPI_EMSMDB_UID

Represents an [ACCT_BIN](acct_bin.md) structure that contains the UID of an Exchange account. 
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x2009  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x20090102  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Get this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md).
  
Use [PROP_ACCT_IS_EXCH](prop_acct_is_exch.md) to verify if the account is an Exchange account. If it is, **PROP_MAPI_EMSMDB_UID** is an **ACCT_BIN** that contains the **emsmdbUID**, which is the unique ID, for the Exchange account. If the account is not an Exchange account, this property is undefined.
  
## See also



[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)


[Using Multiple Exchange Accounts](http://msdn.microsoft.com/library/4e1804bf-4c50-4942-a7ab-9a8caf1be7e5%28Office.15%29.aspx)
  
[PidTagExchangeProfileSectionId Canonical Property](http://msdn.microsoft.com/library/4ad2f417-be8f-4fc8-9321-82097289074b%28Office.15%29.aspx)

