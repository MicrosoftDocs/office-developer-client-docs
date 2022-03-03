---
title: "MAPI Property Identifier Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 957aa00f-23d8-4f3b-bbc2-7d54f17b47b5
 
 
---

# MAPI Property Identifier Overview

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A property identifier is a number that is used to indicate what a property is used for and who is responsible for it. Property identifiers are divided by MAPI into ranges; where an identifier falls in the range indicates its use and ownership. 
  
The range of property identifiers runs from 0x0001 through 0xFFFF. Property identifiers 0x0000 and 0xFFFF are reserved in all cases, meaning that these identifiers must remain unused. The range for properties defined by MAPI runs from 0x0001 to 0x3FFF. These properties are referred to as MAPI-defined properties. The range 0x4000 to 0x7FFF belongs to message and recipient properties, and either clients or service providers can define properties in this range. Properties in the range of 0x0001 to 0x7FFF are referred to as tagged properties. Beyond 0x8000 is the range for what is known as named properties, or properties that include a 32-bit globally unique identifier (GUID) and either a Unicode character string or numeric value. Clients can use named properties to customize their property set.
  
Service providers can define secure profile properties in the range 0x67F0 through 0x67FF. Secure profile properties are used for information that requires additional protection, such as passwords. These properties can be hidden and encrypted. Whether or not secure properties are included in the default list of properties returned by the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method depends on the provider's implementation. Usually these properties are not included. The [IProfSect : IMAPIProp](iprofsectimapiprop.md) interface is used for accessing the properties of a profile section, including secure properties. 
  
Some of the property ranges are restricted to transmittable properties or nontransmittable properties. Transmittable properties are transferred with a message; nontransmittable properties are not transferred with a message. Nontransmittable properties usually contain information that is of value only to clients and service providers operating with the current session. These properties would not necessarily be useful to another messaging system and another set of service providers. The concept of transmittable properties applies primarily to transport providers. To determine whether a property is transmittable or not, pass its property tag to the **FIsTransmittable** macro, defined in the Mapitags.h header file. 
  
For a complete description of the identifier ranges, see [Property Identifier Ranges](property-identifier-ranges.md).
  
## See also



[MAPI Property Overview](mapi-property-overview.md)

