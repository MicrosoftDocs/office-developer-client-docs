---
title: "Creating a Recipient List"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 270f86dd-2c1f-47eb-80f7-9d0d63936d61
description: "Last modified: July 23, 2011"
 
 
---

# Creating a Recipient List

  
  
**Applies to**: Outlook 
  
A recipient list is an [ADRLIST](adrlist.md) structure that contains an array of property value structures for each message recipient — destination for the message. A recipient can represent a human user, a machine, or a folder. All messages to be sent require at least one recipient that has been through the name resolution process — a process for ensuring that the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property is included in the recipient's property value array. 
  
The properties of a recipient are a combination of address book properties and message properties. Recipient properties can apply either to all messages for a particular recipient or only to the current message. Both message store and transport providers can set recipient properties. 
  
Each recipient must have a core set of properties in its property value array by the time the message is ready to be sent. The required set of recipient properties include:
  
- **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md)) 
    
- **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) 
    
- **PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) 
    
- **PR_ENTRYID**
    
- **PR_OBJECT_TYPE** ( [PidTagObjectType](pidtagobjecttype-canonical-property.md)) 
    
- **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) 
    
These properties are used to access the recipient, send messages to it, and to compare it to others. Not all of these properties need to be available right away. You can add a recipient initially without knowing its entry identifier, relying on the name resolution process to assign this property. At some point before you send a message, call [IAddrBook::ResolveName](iaddrbook-resolvename.md) to make sure that all of the recipients in your recipient list are resolved. For more information, see [Resolving a Recipient Name](resolving-a-recipient-name.md).
  
Recipient lists can be created from messaging users or distribution list entries in an address book container or from one-offs. One-offs are recipients that are created either as temporary entries to be used only for addressing a single message or as entries to be added to a personal address book. The format for a one-off entry identifier and address is defined by MAPI. For more information about these formats, see [One-Off Addresses](one-off-addresses.md) and [One-Off Entry Identifiers](one-off-entry-identifiers.md).
  
You can enable users to build their recipient lists:
  
- Only with entries from the address book.
    
- Only with one-off entries.
    
- With a combination of address book recipients and one-offs.
    
 **To create a recipient list using the common address dialog box**
  
1. Allocate an [ADRPARM](adrparm.md) structure and a pointer to an [ADRLIST](adrlist.md) structure. 
    
2. Zero the memory in the **ADRPARM** structure and set the **ADRLIST** pointer to NULL. 
    
3. Call [IAddrBook::Address](iaddrbook-address.md) to display the address dialog box and populate the **ADRPARM** structure. 
    
4. Call [IMessage::ModifyRecipients](imessage-modifyrecipients.md), passing the **ADRLIST** pointer. This structure will contain the properties of each of the recipients selected by the user. 
    
 **To create a recipient list programmatically**
  
1. Allocate an **ADRLIST** structure that contains one [ADRENTRY](adrentry.md) structure for each of the recipients to be included in the list. Make each **ADRENTRY** structure large enough to hold each of the required properties and **PR_RECIPIENT_TYPE** ( [PidTagRecipientType](pidtagrecipienttype-canonical-property.md)).
    
2. For each recipient, set the property value array for its **aEntries** member in the **ADRLIST** structure. 
    
3. Call [IMessage::ModifyRecipients](imessage-modifyrecipients.md) with the MODRECIP_ADD flag set. 
    

