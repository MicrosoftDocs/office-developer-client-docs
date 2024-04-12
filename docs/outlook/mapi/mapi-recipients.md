---
title: "MAPI Recipients"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 88a4360d-6ab8-466e-8ebd-af80227ee00a
 
 
---

# MAPI Recipients

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Every message to be transmitted has one or more recipients, or a set of properties that describe where the message is to be delivered. Because recipients are used only in the context of a message, they are considered subobjects of a message instead of separate MAPI objects. Clients and providers work with recipients using the **IMessage** interface. For more information, see [IMessage : IMAPIProp](imessageimapiprop.md).
  
Clients access a message's recipients through its recipient table. Every message has a recipient table that contains summary information about each of its recipients. The columns included in the table depend on the state of the message. When a message is under composition, its recipients might have only three columns in the table:
  
- Display name, or **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- Recipient type, or **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md))
    
- Row identifier, or **PR_ROWID** ([PidTagRowid](pidtagrowid-canonical-property.md))
    
After the message has undergone the name resolution process, each recipient will also have an entry identifier, or **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) column. And when the message has been submitted, the rows in the recipient table will add two more columns:
  
- Address type, or **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
- Transport responsibility, or **PR_RESPONSIBILITY** ([PidTagResponsibility](pidtagresponsibility-canonical-property.md))
    
Clients can retrieve a message's recipient table by calling its **IMessage::GetRecipientTable** method or its **IMAPIProp::OpenProperty** method. For more information, see [IMessage::GetRecipientTable](imessage-getrecipienttable.md) and [IMAPIProp::OpenProperty](imapiprop-openproperty.md). Message store providers are expected to support both of these approaches. The **OpenProperty** approach requires that the client specify IID_IMAPITable as the interface identifier and **PR_MESSAGE_RECIPIENTS** as the property tag. **PR_MESSAGE_RECIPIENTS** ([PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) is a table object property that represents a message's recipient table. Message store providers are required to set **PR_MESSAGE_RECIPIENTS** for each message and include it in the array of property tags returned from the **IMAPIProp::GetPropList** method. For more information, see [IMAPIProp::GetPropList](imapiprop-getproplist.md).
  
For more information about how to work with a recipient table, see [Recipient Tables](recipient-tables.md).
  
In addition to being used to access a recipient table, **PR_MESSAGE_RECIPIENTS** can be used: 
  
- With **IMAPIProp::CopyTo** or **IMAPIProp::CopyProps** to exclude or include recipients when copying. For more information see, [IMAPIProp::CopyTo](imapiprop-copyto.md) and [IMAPIProp::CopyProps](imapiprop-copyprops.md).
    
- In a subobject restriction to indicate that the child restiction should apply to recipients.
    
Clients can add recipients to a message by copying entries from the MAPI address book or by creating new entries. These new entries, called one-offs, can exist temporarily or be saved permanently in a modifiable container. Whereas recipients that are taken from the address book have entry identifiers associated with their address book provider, one-off recipients have entry identifiers that are formatted by MAPI. Transport providers and clients associate one-off entry identifiers with various types of addresses. 
  
Transport providers call **IMAPISupport::CreateOneOff** to create a one-off entry identifier for an address on an outgoing message when: 
  
- The address belongs to a gateway.
    
- The address cannot be handled by an address book provider in the current profile.
    
For more information, see [IMAPISupport::CreateOneOff](imapisupport-createoneoff.md).
  
Clients call **IAddrBook::CreateOneOff** to create a one-off entry identifier for an address on an incoming message when: 
  
- The address is formatted as a one-off address.
    
- The address is formatted as an Internet address.
    
For more information, see [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md).
  
For more information about one-off entry identifiers and addresses, see [One-Off Entry Identifiers](one-off-entry-identifiers.md) and [One-Off Addresses](one-off-addresses.md).
  
The properties of a recipient are a combination of address book properties and properties specific to recipients. All recipients have the base address properties, assigned by address book providers. When an entry is used as a recipient for an outgoing message, the base address properties are copied to the **ADRLIST** structure that holds the properties for all of a message's recipients. 
  
Two properties that are set specifically for recipients are **PR_RECIPIENT_TYPE** and **PR_RESPONSIBILITY**. **PR_RECIPIENT_TYPE** indicates whether a recipient is a primary, carbon copy, blind carbon copy, or a resend recipient. The first three types are assigned to recipients on messages that are being sent for the first time. 
  
If a recipient does not receive the message and an attempt is made to resend it, the recipient is copied and its type is set to MAPI_P1 to indicate that it is a resend recipient. If only some of the recipients receive a message, their **PR_RECIPIENT_TYPE** properties are marked with the addition of the MAPI_SUBMITTED flag when the message is resent. Clients are required to handle primary recipients, or recipients with their **PR_RECIPIENT_TYPE** set to MAPI_TO. All other types are optional. 
  
 **PR_RESPONSIBILITY** is set to indicate to the transport provider whether or not it should handle sending to the recipient. When an outgoing message is first sent, all of the recipients set **PR_RESPONSIBILITY** to FALSE. As a transport provider claims responsibility for sending to one or more of the recipients, their **PR_RESPONSIBILITY** properties are set to TRUE. 
  

