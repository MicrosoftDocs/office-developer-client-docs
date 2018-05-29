---
title: "PROP_SMTP_SECURE_CONNECTION"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: e316a424-d789-4ce5-bcc6-263049f3659e
description: "Specifies the type of encrypted connection to use for an SMTP account."
---

# PROP_SMTP_SECURE_CONNECTION

Specifies the type of encrypted connection to use for an SMTP account.
  
## Quick info

|||
|:-----|:-----|
|Identifier:  <br/> |0x020A  <br/> |
|Property type:  <br/> |PT_DWORD  <br/> |
|Property tag:  <br/> |0x020A0003  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

The value can be one of the following constants. See [Constants (Account management API)](constants-account-management-api.md) for their values. 
  
|**Constants**|**Description**|
|:-----|:-----|
|**ENCRYPT_CONN_NO_SECURITY** <br/> |Do not use any encryption.  <br/> |
|**ENCRYPT_CONN_SSL** <br/> |Use Secure Socket Layer (SSL) encryption.  <br/> |
|**ENCRYPT_CONN_TLS** <br/> |Use Transport Layer Security (TLS) encryption and authentication protocol.  <br/> |
|**ENCRYPT_CONN_AUTO** <br/> |Automatically detect and use the encryption method supported by the mail server.  <br/> |
   
## See also

- [Managing message downloads for POP3 accounts](managing-message-downloads-for-pop3-accounts.md) 
- [Constants (Account management API)](constants-account-management-api.md)

