---
title: "Sending Messages with TNEF"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 6e2df265-b9dd-4e19-8ca5-3e31804e9120
description: "Last modified: July 23, 2011"
 
 
---

# Sending Messages with TNEF

  
  
**Applies to**: Outlook 
  
Many transport providers automatically send all outgoing messages with the Transport Neutral Encapsulation Format (TNEF). TNEF is used to transmit the formatted text that many clients and message store providers support in their messages, attachments of various types, and custom properties for custom message classes. Although the default mode for most transport providers is to send outgoing messages with TNEF, some transport providers do not support it. The lack of support for TNEF is not an issue for standard messaging clients that send and receive IPM messages. However, for form-based clients or clients that require custom properties, the use of TNEF is essential. Designers of clients that rely on forms or custom properties must be aware of the capabilities of the transport providers that they use.
  
Message recipients can control whether or not a transport provider transmits messages with TNEF by setting the **PR_SEND_RICH_INFO** property. For more information, see **PR_SEND_RICH_INFO** ( [PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)). When a recipient's **PR_SEND_RICH_INFO** property is set to TRUE, a transport provider that supports TNEF transmits it with the message. When the property is set to FALSE, the formatting is discarded. When **PR_SEND_RICH_INFO** does not exist, it is up to the transport provider to choose a default course of action. 
  
When clients and service providers create a custom recipient, they can affect the value of its **PR_SEND_RICH_INFO** property by passing the MAPI_SEND_NO_RICH_INFO flag in the  _ulFlags_ parameter to the **IAddrBook::CreateOneOff** or **IMAPISupport::CreateOneOff** call. For more information, see [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) and [IMAPISupport::CreateOneOff](imapisupport-createoneoff.md). Passing MAPI_SEND_NO_RICH_INFO causes MAPI to set the custom recipient's **PR_SEND_RICH_INFO** property to FALSE; in most cases not passing the flag causes MAPI to set the property to TRUE. The one exception is if the custom recipient's address is interpreted to be an Internet address. In this one situation, MAPI sets **PR_SEND_RICH_INFO** to FALSE. 
  

