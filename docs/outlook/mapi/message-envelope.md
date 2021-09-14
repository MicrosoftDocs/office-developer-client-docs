---
title: "Message Envelope"
manager: lindalu
ms.date: 09/14/2021
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 613956da-c49b-4836-9fde-4601510e8b89
description: "Last modified: September 09, 2021" 
---

# Message Envelope

**Applies to**: Outlook 2013 | Outlook 2016
  
RFC 822 headers are mapped to MAPI properties as follows. PR_SENDER_\* is an abbreviation for the following 5 properties:
  
 **PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md))
  
 **PR_SENDER_ADDRTYPE** ([PidTagSenderAddressType](pidtagsenderaddresstype-canonical-property.md))
  
 **PR_SENDER_EMAIL_ADDRESS** ([PidTagSenderEmailAddress](pidtagsenderemailaddress-canonical-property.md))
  
 **PR_SENDER_SEARCH_KEY** ([PidTagSenderSearchKey](pidtagsendersearchkey-canonical-property.md))
  
 **PR_SENDER_ENTRYID** ([PidTagSenderEntryId](pidtagsenderentryid-canonical-property.md))
  
Similar abbreviations are used for PR_SENT_REPRESENTING_\* and other groups of message properties.
  
|**SMTP header**|**MAPI property**|
|:-----|:-----|
|From:  <br/> |Outbound: PR_SENDER_\*; inbound: PR_SENDER_\* and PR_SENT_REPRESENTING_\*  <br/> |
|Date:  <br/> |Outbound: current time; inbound: **PR_MESSAGE_DELIVERY_TIME** ([PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md))  <br/> |
|To:  <br/> |**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) and **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) for recipients where **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) is MAPI_TO  <br/> |
|Cc:  <br/> |**PR_DISPLAY_NAME** and **PR_EMAIL_ADDRESS** for recipients where **PR_RECIPIENT_TYPE** is MAPI_CC  <br/> |
|Bcc:  <br/> |**PR_DISPLAY_NAME** and **PR_EMAIL_ADDRESS** for recipients where **PR_RECIPIENT_TYPE** is MAPI_BCC  <br/> |
|||
|Received:  <br/> |No corresponding MAPI property; put local host name and your component name here  <br/> |
|Return-receipt-to:  <br/> |**PR_REPORT_NAME** ([PidTagReportName](pidtagreportname-canonical-property.md)) and **PR_REPORT_ENTRYID** ([PidTagReportEntryId](pidtagreportentryid-canonical-property.md))  <br/> |
|Reply-to:  <br/> |**PR_REPLY_RECIPIENT_ENTRIES** ([PidTagReplyRecipientEntries](pidtagreplyrecipiententries-canonical-property.md)) and **PR_REPLY_RECIPIENT_NAMES** ([PidTagReplyRecipientNames](pidtagreplyrecipientnames-canonical-property.md))  <br/> |
|Subject:  <br/> |**PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md)) No particular length limitation.  <br/> |
|MIME-version:  <br/> |Always "1.0"  <br/> |
|||
|X-MS-Attachment:  <br/> |For compatibility with MS Mail SMTP gateway. _filename size mm-dd-yyy hh:mm_Details below.  <br/> |
|||
| _entire SMTP message envelope_ <br/> |**PR_TRANSPORT_MESSAGE_HEADERS** ([PidTagTransportMessageHeaders](pidtagtransportmessageheaders-canonical-property.md))  <br/> |
|header name TBD  <br/> |**PR_SEND_RICH_INFO** ([PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)) _for sender only._The TBDheader should be used to determine whether the sender is capable of interpreting TNEF content in a reply.  <br/> |
|MessageID:  <br/> |**PR_TNEF_CORRELATION_KEY** ([PidTagTnefCorrelationKey](pidtagtnefcorrelationkey-canonical-property.md))  <br/> |
|Content-type  <br/> |Either text/plain or multipart/mixed. See "Message Content" section.  <br/> |
   
The X-MS-Attachment header is formatted as four tokens, separated by a space:
  
 _name size date time_
  
The first token is the filename, which may contain embedded spaces, so this header should be parsed from the right on inbound messages. The size is in bytes; the date is formatted as  _mm-dd-yyyy,_ and the time as  _hh:mm._
  
> [!NOTE]
> MessageID is not mapped to **PR_SEARCH_KEY** because the SMTP domain has specific requirements on the format of the message identifier which make it impossible to encode an arbitrary MAPI message identifier. Instead, MessageID is mapped to **PR_TNEF_CORRELATION_KEY**. This property is a transport-defined property that is set by the transport sending an outbound message and used by a transport receiving an inbound message. For more information, see [Developing a TNEF-Enabled Transport Provider](developing-a-tnef-enabled-transport-provider.md).
