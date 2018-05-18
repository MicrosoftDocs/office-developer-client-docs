---
title: "PidTagNextSendAcct"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 1cf5b314-39fa-996f-fd88-00380ffbc4de
description: "Specifies the secondary accountsendstamp for the message."
---

# PidTagNextSendAcct

Specifies the secondary account "send" stamp for the message.
  
## Quick info

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_NEXT_SEND_ACCT  <br/> |
|Identifier:  <br/> |0x0E29  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Outlook application  <br/> |
   
## Remarks

This property applies to a MAPI message object. For a received message, the secondary account "send" stamp indicates which account a forward or a reply should be sent with, if the forward or reply cannot be sent with the primary account. For an outgoing message, the secondary account "send" stamp determines with which account to send the message, if the message cannot be sent with the primary account. Its value is the [PROP_ACCT_SEND_STAMP](prop_acct_send_stamp.md) value from the [IOlkAccount](iolkaccount.md) interface of the account with which the message is being sent. 
  
## See also



[Constants (Account management API)](constants-account-management-api.md)


[MAPI Properties](http://msdn.microsoft.com/library/3b980217-b65b-442b-8c18-b8b9f3ff487a%28Office.15%29.aspx)
  
[PidTagNextSendAcct Canonical Property](http://msdn.microsoft.com/library/b7429c2e-0d9d-4921-9f56-9ecad817f8cb%28Office.15%29.aspx)

