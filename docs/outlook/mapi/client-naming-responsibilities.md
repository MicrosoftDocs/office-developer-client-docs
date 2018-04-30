---
title: "Client Naming Responsibilities"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: dbb6ba5f-18c8-426f-9f50-ce6f2fd1dc5b
description: "Last modified: March 09, 2015"
---

# Client Naming Responsibilities

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Clients must follow a naming convention for their properties that need to be translated by a gateway. All properties to be translated should be created as named properties in one of the five property sets designated to hold mappable properties:
  
PS_ROUTING_EMAIL_ADDRESSES
  
PS_ROUTING_ADDRTYPE
  
PS_ROUTING_DISPLAY_NAME
  
PS_ROUTING_ENTRYID
  
PS_ROUTING_SEARCH_KEY
  
Addressing properties that relate to the same user must be given the same name. Gateways rely on this naming convention, which enables them to match an address with its correct address type. For address parsing, the mapping between address and address type must be accurate.
  
MAPI named properties are represented with the **MAPINAMEID** data structure, which specifies that the property name can be either a Unicode string or a 32-bit integer. For more information, see [MAPINAMEID](mapinameid.md). Integer naming is recommended for groups of addresses because it is a straightforward way to differentiate between sets of mappable properties, and it can easily serve as an index to the user. The alternative to using integers is to assign one string as the name for all five of a user's mappable properties. If only one user requires mapping, assigning a string is acceptable. However, when there are multiple users, it is better to use integer naming. The name, whether it be numeric or string-based, should be stored in either a message class-specific property or in a property belonging to a property set that is defined by the client application. 
  
> [!NOTE]
> Avoid translating integer names to strings, such as "route_recipient_1" and "route_recipient_2." This effort is unnecessary. 
  
To illustrate how this naming convention works, consider a routing application that sends a message to each member of a four-person team. When one member receives the message, he or she must respond to it before it can be sent along with the compiled responses to the next member. The original message contains a recipient list with one entry: the first member of the team. Embedded within the message are the gateway-mappable properties for the other three team members. Each member has five core user properties residing in the gateway-mappable property sets, that are assigned a unique number as a name. 
  
The following table illustrates the settings for each set of gateway-mappable properties stored for the three remaining team members to whom the message is routed when the first team member is finished with it.
  
|**Property Set**|**Second Team  <br/> Member**|**Third Team  <br/> Member**|**Fourth Team  <br/> Member**|
|:-----|:-----|:-----|:-----|
|PS_ROUTING_EMAIL_ADDRESSES  <br/> |Address = 0  <br/> |Address = 1  <br/> |Address = 2  <br/> |
|PS_ROUTING_ADDRTYPE  <br/> |Address type = 0  <br/> |Address type = 1  <br/> |Address type = 2  <br/> |
|PS_ROUTING_DISPLAY_NAME  <br/> |Display name = 0  <br/> |Display name = 1  <br/> |Display name = 2  <br/> |
|PS_ROUTING_ENTRYID  <br/> |Entry identifier = 0  <br/> |Entry identifier = 1  <br/> |Entry identifier = 2  <br/> |
|PS_ROUTING_SEARCH_KEY  <br/> |Search key = 0  <br/> |Search key = 1  <br/> |Search key = 2  <br/> |
   
Clients that use mappable search keys as references to other message properties must recognize that the other message properties will not be translated unless they are placed in one of these mappable property sets. When a message with unmapped references to mapped search keys is sent to a destination in another messaging domain, the references are invalid. To enable these other properties to remain synchronized with the search keys, you can assign them string names in the PS_ROUTING_SEARCH_KEY property set that do not interfere with the names given to any of the core mappable properties. For example, suppose a client needs to transmit a property that contains the search key for the last person in a long routing list. The client can create a named property in the PS_ROUTING_SEARCH_KEY property set called "last_search_key." Because it is stored in a mappable property set, the "last_search_key" property is translated along with the rest of the gateway-mappable properties.
  

