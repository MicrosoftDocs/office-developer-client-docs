---
title: "PROP_MAPI_IDENTITY_ENTRYID"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: c64db8ea-d6ad-4fb9-97aa-958e5a0daf8f
description: "Retrieves or sets the address book entry ID for the account."
---

# PROP_MAPI_IDENTITY_ENTRYID

Retrieves or sets the address book entry ID for the account.
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x2002  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x20020102  <br/> |
|Access:  <br/> |Read/write  <br/> |
   
## Remarks

 **PROP\_MAPI\_IDENTITY\_ENTRYID** is not expected to exist on every account. For example, an Exchange account could have **PROP\_MAPI\_IDENTITY\_ENTRYID** set and not [PROP\_ACCT_USER_EMAIL_ADDR](prop_acct_user_email_addr.md), while for an SMTP/POP3 account the situation is reversed. **PROP\_MAPI_IDENTITY_ENTRYID** returns an entry ID that is similar to the value returned by  _lppEntryID_ in [IMAPISession::QueryIdentity](http://msdn.microsoft.com/library/a2cdda90-5457-49a7-b98c-7273ffe5cbbc%28Office.15%29.aspx). 
  
## See also

- [About the Account Management API](about-the-account-management-api.md)

