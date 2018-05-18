---
title: "Providing Read and Nonread Reports for Message Store Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9644b8c5-ecc0-4ea3-972a-2169c78b99e5
description: "Last modified: July 23, 2011"
 
 
---

# Providing Read and Nonread Reports for Message Store Providers

  
  
**Applies to**: Outlook 
  
If a message store provider can receive messages, it is required to support read reports and nonread reports of messages received by the message store provider. If a received message contains the **PR_READ_RECEIPT_REQUESTED** ([PidTagReadReceiptRequested](pidtagreadreceiptrequested-canonical-property.md)) property and that property's value is TRUE, the message store should send a notification message to the sender when the user opens the message, indicating that the message has been read. Similarly, if the user deletes the message before opening it, the message store should issue a reply to the sender indicating that the message was not read.
  
Issuing these reports is a matter of creating an [IMessage : IMAPIProp](imessageimapiprop.md) object, filling out the relevant properties on the message, and submitting it to the MAPI spooler as if the message had originated with the user. The [IMAPISupport::ReadReceipt](imapisupport-readreceipt.md) method can be used for this. 
  
> [!NOTE]
> Special care must be taken when a message store makes copies of an unread message with pending read or nonread reports. Such reports should not be generated when users read any copies of a message for which reports have been requested. When making a copy of such a message, the message store provider should include the CLEAR_RN_PENDING and CLEAR_NRN_PENDING flags in its calls to [IMAPIFolder::SetReadFlags](imapifolder-setreadflags.md) and [IMessage::SetReadFlag](imessage-setreadflag.md). 
  
## See also



[Message Store Features](message-store-features.md)

