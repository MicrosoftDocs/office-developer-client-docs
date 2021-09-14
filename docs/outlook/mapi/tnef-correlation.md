---
title: "TNEF Correlation"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 93d1716d-a0be-45aa-85d2-6c9be65f5fd2
description: "Last modified: March 12, 2013"
 
 
---

# TNEF Correlation

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Some messaging systems perform a correlation check on any Transport-Neutral Encapsulation Format (TNEF) stream attached to an inbound message to verify that the TNEF stream does in fact belong to that message. This involves matching the value of some field in the header of the inbound message with a copy of that value stored in some property in the TNEF stream. Values that are presumably unique for each message, such as message ID numbers, are typically used for this. The transport or gateway that created the TNEF stream is responsible for choosing an appropriate value from the message header and placing a copy into an appropriate property before encoding the outgoing message's properties into the TNEF stream. Gateways or transports that receive the message can then extract that property from the TNEF stream and verify that its value matches the value of the corresponding header field on the inbound message.
  
If the values do not match, the gateway or transport should discard the TNEF stream and process only the native message envelope. Such checks are prudent because non-MAPI-based mail clients may attach a file that contains a TNEF stream from an old message to a forwarding or even an unrelated message; if not checked, such an error may cause the loss of message text.
  
The header field value chosen must be unique to the message. There is no fixed header field for all messaging systems because different messaging systems use different header fields, but typically the messaging system assigns a unique identifier to the message which is suitable for this purpose. For example, SMTP systems typically use the MessageID header, while X.400 systems typically use the IM_THIS_IPM attribute.
  

