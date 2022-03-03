---
title: "Property Identifiers and Types"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 39a5c97c-5ac8-47a8-b193-a4b3ba6a02a5
 
 
---

# Property Identifiers and Types

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
All MAPI properties are represented by property tags. A property tag is a 32-bit unsigned integer value that contains the property's identifier in the high order 16 bits and the property's type in the low order 16 bits. Property tags for all of the properties defined by MAPI are included in the mapitags.h header file.
  
Property identifiers are used to indicate what a property is used for and who is responsible for it. Property identifiers are divided by MAPI into ranges; where an identifier falls in the range indicates its use and ownership. 
  
Property types are used to indicate the format of the property's data. MAPI defines all of the valid types. Clients and service providers creating new properties must use one of these types. All of the property types are included in the mapidefs.h header file.
  

