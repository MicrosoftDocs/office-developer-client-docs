---
title: "Recipient Tables"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 02e77317-54c4-4fca-9ab4-835998ce07ce
description: "Last modified: July 23, 2011"
 
 
---

# Recipient Tables

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The recipient table contains information about all the recipients for a message. Message store providers implement recipient tables and client applications use them. Clients access a recipient table by making a call to the [IMessage::GetRecipientTable](imessage-getrecipienttable.md) method, or if the message store provider supports it, to the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method. Clients access recipient tables with **OpenProperty** by specifying **PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) for the property tag and IID_IMAPITable for the interface identifier. Changes to a recipient table can be made by calling the [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method. 
  
Recipient tables have a different column set depending on whether the message has been submitted. The following properties make up the required column set in recipient tables:
  
- **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- **PR_RECIPIENT_TYPE** ( [PidTagRecipientType](pidtagrecipienttype-canonical-property.md))
    
- **PR_ROWID** ( [PidTagRowid](pidtagrowid-canonical-property.md))
    
The optional properties are:
  
- **PR_DISPLAY_TYPE** ( [PidTagDisplayType](pidtagdisplaytype-canonical-property.md))
    
- **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md))
    
- **PR_SPOOLER_STATUS** ( [PidTagSpoolerStatus](pidtagspoolerstatus-canonical-property.md))
    
- **PR_OBJECT_TYPE** ( [PidTagObjectType](pidtagobjecttype-canonical-property.md))
    
Submitted messages should include these additional properties in their required column set:
  
- **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
- **PR_RESPONSIBILITY** ( [PidTagResponsibility](pidtagresponsibility-canonical-property.md))
    
Depending on a provider's implementation, additional columns, such as **PR_SENDER_NAME** ( [PidTagSenderName](pidtagsendername-canonical-property.md)) and [ENTRYID](entryid.md), might be in the table.
  
Any message store provider that supports message transmission — as indicated by the STORE_SUBMIT_OK bit being set in the provider's **PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property — should offer support for a particular set of restrictions in a recipient table implementation. The **AND**, **OR**, exist, and property restrictions are among the types of restrictions that should be available to recipient table users. Only the equal and not equal operators need to be supported on the property restriction. These restrictions must work with the following properties:
  
- **PR_ADDRTYPE**
    
- **PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) 
    
- **PR_RECIPIENT_TYPE**
    
- **PR_RESPONSIBILITY**
    
- **PR_SPOOLER_STATUS**
    
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

