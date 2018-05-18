---
title: "MAPI Address Book"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 6703ba3f-54a5-4059-b10a-1d42a9e81be1
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Address Book

  
  
**Applies to**: Outlook 
  
The integrated address book is an object that MAPI implements to provide access to an integrated collection of addressing information from all of the address book providers in the profile. With the address book, client applications and service providers do not have to differentiate between the unique addressing schemes of messaging systems. Instead, they can look up the addresses of any recipients in any messaging system, as long as the address book provider for the messaging system is installed.
  
The address book can be accessed programmatically, without user intervention, or interactively through the use of common dialog boxes. MAPI includes dialog boxes to display a summary list of the entries in the address book, detailed information about a particular recipient, a warning when a user creates a recipient that cannot be mapped to a unique address, and a set of template forms for creating new recipients.
  
The MAPI address book is similar in structure to a message store in that it is organized hierarchically. The address book provides access to three types of objects implemented by an address book provider:
  
- An address book container object.
    
- A distribution list object.
    
- A messaging user object.
    
Each of these types of objects is accessed through its unique entry identifier that is assigned by its address book provider. 
  
Address book containers are similar to folders in that they hold objects of different types. An address book container can hold other address book containers as well as messaging user and distribution list objects. Address book containers are used to organize and store address book objects.
  
To achieve the address book's integrated appearance, address book providers expose zero, one, or more of their top-level containers to MAPI which merges them and displays the results under a single top-level container. Address book providers can choose to expose one set of containers for one type of messaging session and a different set for another session. It is also possible for address book providers to have no top-level containers and expose only a list of templates that can be used to create recipients.
  
Message recipients are implemented with messaging user and distribution list objects. Messaging users are individual recipients; distribution lists are group recipients. Each messaging user has a unique address of a particular type handled by a particular messaging system. A distribution list is a named collection of recipients. Distribution lists can contain messaging user objects and other distribution lists. When a user of a client application sends a message to a distribution list, the message is being sent to each of the list's messaging user members. 
  
Messaging users and distribution lists have a set of five properties that are known as the base address properties. These are required properties and are briefly described as follows.
  
|**Base address property**|**Description**|
|:-----|:-----|
|**PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))  <br/> |Type of address for the recipient. Each address type follows a particular format and is used with a particular messaging system.  <br/> |
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Displayable name for the recipient.  <br/> |
|**PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md))  <br/> |Address of the recipient.  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Entry identifier used to access the recipient.  <br/> |
|**PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md))  <br/> |Binary comparable key used to identify the recipient.  <br/> |
   
MAPI defines many groups of properties that are variations of the base address properties. These other groups describe messaging users and distribution lists in different situations. For example, one group of properties describes the delegate sender of a message and another group the delegate recipient.
  

