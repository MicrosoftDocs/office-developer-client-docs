---
title: "Defining New MAPI Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 1a2325ea-ddfa-480f-b65f-f5b20471fb40
 
 
---

# Defining New MAPI Properties

**Applies to**: Outlook 2013 | Outlook 2016
  
In spite of the wealth of properties supplied by MAPI for use by clients and service providers, MAPI enables new properties to be created if necessary. Some of the valid scenarios for defining new public properties include a client creating properties to support a new message class and a service provider creating new properties to expose unique messaging system features.
  
It is typically not valid for a service provider to define new properties for an existing MAPI object or message class. One of the primary benefits of using MAPI is that standard identifiers and formats for a large number of messaging system elements are set up, enabling users to seamlessly mix and match service providers. Service providers that use nonstandard properties do not work as well with other service providers.
  
Clients can create content properties for new message classes by:
  
- Using property identifiers within a designated range for message class-specific content properties.

  - Or -

- Using named properties.

The first option is preferable because not all service providers support named properties. MAPI defines two separate ranges for clients to use for new message class-specific content properties:
  
- 0x6800 to 0x7BFF for transmittable properties

- 0x7C00 to 0x7FFF for nontransmittable properties

Property identifiers must fall in predefined ranges to help prevent collisions between properties defined by different vendors or users. However, users of properties in these ranges cannot make assumptions as to the behavior of the properties. Every client that creates a new message class has access to these ranges; a property with identifier _xxxx_ can mean one behavior for one message class and another behavior for another message class.
  
Named properties are used to guarantee a specific property is unique to a message class. Named property identifiers start in the 0x8000 range. Clients define one or more names and then call the message store's [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method to associate an identifier with each name. Named properties can be used by clients or service providers to define new properties for any object only if the owner of the object supports named properties. Users of these properties call **GetIDsFromNames** and a related **IMAPIProp** method, [GetNamesFromIDs](imapiprop-getnamesfromids.md), to map between a name and its identifier.
  
All properties, new or existing, must use the set of predefined property types. New property types cannot be added and existing types cannot be modified or deleted. Simple, small properties, such as single-character or 16-bit integer properties, can be stored in any appropriate type. For example, integers can be stored as **ULONG** and strings can be stored as **PT_STRING8**.
  
Use the **PT_BINARY** type to indicate a counted byte array. This property type is useful for extending the types of data that can be stored in an object. Bytes are transmitted in sequence and no assumptions are made about the meaning of the data. When a client application reads data out of such a property, the data is unchanged from how it was stored. The client must perform any necessary byte swapping when moving data across CPUs.
  
## See also

[MAPI Property Overview](mapi-property-overview.md)
