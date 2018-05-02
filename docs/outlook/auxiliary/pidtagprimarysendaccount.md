---
title: "PidTagPrimarySendAccount"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: e1bc4900-d261-f692-386b-139ef6960212
description: "Specifies the primary accountsendstamp for a message."
 
 
---

# PidTagPrimarySendAccount

Specifies the primary account "send" stamp for a message.
  
## Quick Info

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PRIMARY_SEND_ACCOUNT  <br/> |
|Identifier:  <br/> |0x0E28  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Account  <br/> |
   
## Remarks

This property applies to a MAPI message object. For a received message, the primary account "send" stamp indicates which account a forward or a reply should be sent with. For an outgoing message, it determines which account to send the message with. Its value is the [PROP_ACCT_SEND_STAMP](prop_acct_send_stamp.md) value from the [IOlkAccount](iolkaccount.md) interface of the account with which the message is being sent. 
  
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
#### Other resources

[MAPI Properties](http://msdn.microsoft.com/library/3b980217-b65b-442b-8c18-b8b9f3ff487a%28Office.15%29.aspx)
  
[PidTagPrimarySendAccount Canonical Property](http://msdn.microsoft.com/library/2f268b3b-2e4c-4aea-8879-bdd0ac1df35c%28Office.15%29.aspx)

