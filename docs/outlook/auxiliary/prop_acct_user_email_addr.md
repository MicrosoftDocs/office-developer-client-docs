---
title: "PROP_ACCT_USER_EMAIL_ADDR"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: fe447899-d37a-4775-a09d-13ba3a878008
description: "Specifies the email address for the account."
---

# PROP_ACCT_USER_EMAIL_ADDR

Specifies the email address for the account.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x000C  <br/> |
|Property type:  <br/> |PT_UNICODE  <br/> |
|Property tag:  <br/> |0x000C001F  <br/> |
|Access:  <br/> |Read/write  <br/> |
   
## Remarks

 **PROP_ACCT_USER_EMAIL_ADDR** is not expected to exist on every account. For example, an Exchange account could have [PROP_MAPI_IDENTITY_ENTRYID](prop_mapi_identity_entryid.md) but not **PROP_ACCT_USER_EMAIL_ADDR**, while for an SMTP/POP3 account, the situation is reversed.
  
## See also



[About the Account Management API](about-the-account-management-api.md)

