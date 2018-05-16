---
title: "Message Properties Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 447f54de-9f0d-4f73-89b6-bed9cfea9c15
description: "Last modified: July 23, 2011"
 
 
---

# Message Properties Overview

  
  
**Applies to**: Outlook 
  
MAPI divides message properties into three types:
  
- Message content properties.
    
- Message transmission, or envelope, properties.
    
- Message recipient properties.
    
Message content properties describe the text of a message. Every message class has its own set of content properties. MAPI defines content properties for note and report messages; it is up to the clients and message store providers that handle these classes of messages to set the properties appropriately for their implementations. **PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md)) and **PR_RTF_COMPRESSED** ( [PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) are examples of content properties for note messages. **PR_BODY** contains the unformatted contents of a note, while **PR_RTF_COMPRESSED** contains the compressed version of a note's formatted contents. For more information about property identifier ranges, see [Property Identifier Ranges](property-identifier-ranges.md).
  
For new message classes, clients can define content-specific properties in one of two ways:
  
- By using property identifiers in the custom message class content properties range: 0x6800 through 0x7BFF.
    
- By using named properties that have identifiers that fall in the 0x8000 through 0xFFFE range.
    
The identifier range for custom message class content properties is available to any client that creates a custom message class. Therefore, one property identifier in this range can be used for multiple message classes. Users of properties in this range cannot make assumptions as to the behavior of the properties. 
  
For named properties, clients create a name that specifies a property set and either a character string or a numeric value for each new property. Clients then associate the property with an identifier in the named property range. Users of named properties access them by name or identifier through the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) and [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) methods. 
  
Envelope properties provide information that is used to transmit a message from one recipient to another. As with message content properties, it is possible for clients or service providers to define their own envelope properties to supplement those that MAPI defines. Clients and transport providers set the envelope properties that MAPI defines based on the definition that MAPI provides. Transport providers that implement special features can define their own envelope properties to expose those features to clients. MAPI sets aside a range of property identifiers that can be used for these special provider-defined properties. Transport providers typically implement a special property page to display these properties and enable clients to change them. **PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md)) and **PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md)) are examples of envelope properties. For more information, see [Property Identifier Ranges](property-identifier-ranges.md).
  
Recipient properties describe the destination for a sent message. A recipient can be a messaging user, distribution list, or a computer. Recipient properties are defined by MAPI and set by service providers. Some recipient properties are supported by address book providers for their messaging user and distribution list objects; other recipient properties are supported by clients, message store providers, or transport providers. For example, all recipients require an address and an address type; these are properties maintained by an address book provider when the recipient is stored in one of its containers. Recipients also have a type, **PR_RECIPIENT_TYPE** ( [PidTagRecipientType](pidtagrecipienttype-canonical-property.md)), which identifies a recipient as either a primary, carbon copy, or blind carbon copy recipient.
  
Many message properties are optional, meaning that clients cannot expect them to be available or set to valid values. Some message properties are required but available only when a message is in a particular state. For example, a newly created message is not required to have an entry identifier until after the message has been saved, and it is not required to have a message class until the message is ready to be submitted. Clients should always check the results of their [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPIProp::OpenProperty](imapiprop-openproperty.md) calls and have default values ready as a backup in case a requested property is unavailable. 
  
Most message properties that service providers set are read-only to clients. 
  
## See also

#### Concepts

[MAPI Messages](mapi-messages.md)

