---
title: "Property Names and Property Sets"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: cb216f5c-c965-4372-a15b-82090a410266
description: "Last modified: July 23, 2011"
 
 
---

# Property Names and Property Sets

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The name of every named property has two parts:
  
- A globally unique identifier, or GUID, that specifies a property set.
    
- A Unicode character string or 32-bit numeric value. 
    
Names of named properties are described using a [MAPINAMEID](mapinameid.md) structure. This structure contains a property set member, a member for specifying the name in either numeric or string format, and a member for identifying which format is used. Because the property set is part of the property's name, it is not optional. MAPI has defined several property sets for use by clients and service providers, but if an existing property set is inappropriate, a new property set can be defined. Clients and service providers can define their own property sets by calling [CoCreateGUID](http://msdn.microsoft.com/en-us/library/ms688568.aspx) function. Typically these property sets are created for custom client applications. 
  
MAPI's property sets are represented by the following constants:
  
PS_MAPI
  
PS_PUBLIC_STRINGS
  
PS_ROUTING_EMAIL_ADDRESSES
  
PS_ROUTING_ADDRTYPE
  
PS_ROUTING_SEARCH_KEY
  
PS_ROUTING_DISPLAY_NAME
  
PS_ROUTING_ENTRYID
  
The PS_MAPI property set is reserved; it is used by service providers to generate names for properties with identifiers below the named property range. The PS_PUBLIC_STRINGS property set is used by clients for named properties of IPM messages. Because named properties in the PS_PUBLIC_STRINGS property set appear in a client's user interface, nonvisible messages such as those that belong to the IPC message class should avoid creating named properties with this property set. Instead, they should create properties in the message class-specific range, 0x6800 through 0x7FFF.
  
The other property sets hold named properties describing recipients that are typically members of a routing list. Containing the same type of information as the properties that are associated with recipient list properties, properties in these property sets are understood by gateways to require mapping for a target messaging system. Because there are five types of information for describing properties, MAPI has defined five different property sets. A client sending a message that must include an address and address type for its routing list members assigns a named property for each member in the PS_ROUTING_EMAIL_ADDRESSES and PS_ROUTING_ADDRTYPE property sets. This ensures that the address and address type remain viable when sent to a foreign messaging system.
  
## See also



[MAPI Named Properties](mapi-named-properties.md)

