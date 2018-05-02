---
title: "PROP_SMTP_AUTH_METHOD"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 4202cafc-9011-406d-90b3-8dabf531c90b
description: "Specifies the authentication method to use for the SMTP account."
 
 
---

# PROP_SMTP_AUTH_METHOD

Specifies the authentication method to use for the SMTP account.
  
## Quick Info

|||
|:-----|:-----|
|Identifier:  <br/> |0x0208  <br/> |
|Property type:  <br/> |PT_DWORD  <br/> |
|Property tag:  <br/> |0x02080003  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

The value is a bitmask of the following constants. See [Constants (Account management API)](constants-account-management-api.md) for their values. 
  
- **SMTP_AUTH_SAME_AS_POP** means using the same credentials as my incoming mail server, as provided by [PROP_INET_USER](prop_inet_user.md) and [PROP_INET_PASSWORD](prop_inet_password.md).
    
- **SMTP_AUTH_USER_PASS** means using the credentials as provided by [PROP_SMTP_USER](prop_smtp_user.md) and [PROP_SMTP_PASSWORD](prop_smtp_password.md).
    
- **SMTP_AUTH_RECEIVE_BEFORE_SEND** means requesting the user to log on to the incoming mail server before sending mail. 
    
## See also

#### Concepts

[Managing message downloads for POP3 accounts](managing-message-downloads-for-pop3-accounts.md)
  
[Constants (Account management API)](constants-account-management-api.md)

