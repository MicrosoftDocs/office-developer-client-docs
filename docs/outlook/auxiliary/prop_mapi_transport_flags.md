---
title: "PROP_MAPI_TRANSPORT_FLAGS"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 12cfe096-6882-c0be-b248-87567cb71e83
description: "Represents transport settings that Outlook uses to determine the necessary synchronization tasks and to disable the user interface (UI) elements that the account does not support."
---

# PROP_MAPI_TRANSPORT_FLAGS

Represents transport settings that Outlook uses to determine the necessary synchronization tasks and to disable the user interface (UI) elements that the account does not support.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x2010  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x20100102  <br/> |
|Access:  <br/> |Read/write  <br/> |
   
## Remarks

Get or set this property by using [IOlkAccount::GetProp](iolkaccount-getprop.md) or [IOlkAccount::SetProp](iolkaccount-setprop.md), respectively.
  
Returns **MAPIACCT_SEND_ONLY** if the account can only send messages but cannot receive messages. In this case, Outlook disables UI that does not apply to this type of accounts (for example, the UI for **Send/Receive**).
  
## See also



[About the Account Management API](about-the-account-management-api.md)
  
[Constants (Account management API)](constants-account-management-api.md)

