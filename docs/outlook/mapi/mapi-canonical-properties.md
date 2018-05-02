---
title: "MAPI Canonical Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 29151beb-7436-401a-8072-58d4facd8458
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Canonical Properties

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A canonical property is a virtual property that represents a MAPI property, or multiple MAPI properties defined with the same property identifier. Canonical properties are only intended to facilitate consistent identification of MAPI properties in discussions or documentation outside of code. Unlike MAPI-defined tagged property names, canonical property names are not defined as global constants in MAPI header files.
  
## Naming Conventions

Canonical property names begin with a prefix, "Pid", which represents "property identifier." Depending on whether the property is a tagged property, a named property with a numerical identifier, or a named property with a string name, the prefix is further qualified as "PidTag," "PidLid," and "PidName" respectively. For example, [PidTagAccount](pidtagaccount-canonical-property.md) represents the tagged properties, **PR_ACCOUNT** ( [PidTagAccount](pidtagaccount-canonical-property.md)), **PR_ACCOUNT_A** ( [PidTagAccount](pidtagaccount-canonical-property.md)), and **PR_ACCOUNT_W** ( [PidTagAccount](pidtagaccount-canonical-property.md)), that specify a recipient's account name; [PidLidContacts](pidlidcontacts-canonical-property.md) represents the **dispidContacts** property, a named property that has a numerical identifier and that specifies the name of contacts associated with a message; and [PidNamePhishingStamp](pidnamephishingstamp-canonical-property.md) represents "http://schemas.microsoft.com/outlook/phishingstamp," a named property that has a string name, and that specifies the string marking messages that are likely to be phishing. 
  
## Representing Similar Properties Using One Canonical Property

### Identifying Properties in MAPI

All properties in MAPI are identified by a property identifier that is an unsigned 16-bit value. The property identifier and the property type (another unsigned 16-bit value) constitute a property tag for the property. 
  
MAPI uses a property tag to uniquely define properties. Properties that have the same property tag, like **PR_BUSINESS2_TELEPHONE_NUMBER** ( [PidTagBusiness2TelephoneNumber](pidtagbusiness2telephonenumber-canonical-property.md)) and **PR_OFFICE2_TELEPHONE_NUMBER** ( [PidTagBusiness2TelephoneNumber](pidtagbusiness2telephonenumber-canonical-property.md)), are considered identical properties in MAPI. For a list of property tags that MAPI has defined for its own properties, see the MAPI header file, Mapitags.h.
  
Note that MAPI divides property identifiers into ranges. Where an identifier falls in the range indicates its use and ownership. The property identifiers of tagged properties fall in the range of 0x0001 to 0x7FFF. Within this range are the property identifiers of MAPI-defined properties, which fall in the range of 0x0001 to 0x3FFF. The property identifiers of named properties fall in the range from 0x8000 to 0x8FFF. 
  
Named properties are additionally attributed by a property set, and either a long ID (LID), which is an unsigned 32-bit value, or a string. A property set is a GUID that identifies a group of named properties with a similar purpose. The property set and LID or string name are used to get or set the named property.
  
### Property Type

Aside from identifiers, a property is attributed by a data type that specifies the type of values allowed for that property.
  
For properties that are of the string type, depending on the support for Unicode in the underlying platform, the property can be of type PT_STRING8 (null-terminated 8-bit character string) or PT_UNICODE (null-terminated Unicode string). A property can be defined with the PT_TSTRING type, and depending on compilation settings, PT_TSTRING defaults to a Unicode string for platforms that support Unicode, or to a PT_STRING8 string for platforms that support ANSI or DBCS. It is common that a string-typed property is identified by three similar names, such as **PR_ACCOUNT**, **PR_ACCOUNT_A**, and **PR_ACCOUNT_W**, which are of the type PT_TSTRING, PT_STRING8, and PT_UNICODE respectively.
  
For more information on property types and macros related to types, see the MAPI header file, Mapidefs.h.
  
### Identifying Similar Properties

In the current MAPI property landscape, it is not uncommon to find that a property has been exposed under different property names, all of which are defined with the same property identifier. For example, the tagged properties, **PR_BUSINESS2_TELEPHONE_NUMBER** and **PR_OFFICE2_TELEPHONE_NUMBER**, are defined in Mapitags.h to have the same property identifier and type. Closely related to these two properties are:
  
- **PR_BUSINESS2_TELEPHONE_NUMBER_A**
    
- **PR_BUSINESS2_TELEPHONE_NUMBER_W**
    
- **PR_OFFICE2_TELEPHONE_NUMBER_A**
    
- **PR_OFFICE2_TELEPHONE_NUMBER_W**
    
The properties with the "_A" suffix are typed as PT_STRING8, and those with the "_W" suffix are typed as PT_UNICODE.
  
The purpose of a canonical property, **PidTagBusiness2TelephoneNumber** in this example, is to facilitate referencing such closely affiliated MAPI properties using one identifier, and in a consistent way (using the "Pid" prefix) across all MAPI properties. To find which real MAPI properties a canonical property represents, see [Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md). To find the canonical property that a MAPI property is associated with, see [Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md).
  
## MAPI Support of Canonical Property Names

Because canonical properties are not real properties and are not defined in MAPI header files, you should not use canonical property names in code; instead, you should continue to use the exact MAPI property names in code. For example, you can refer **PR_BUSINESS2_TELEPHONE_NUMBER** and **PR_OFFICE2_TELEPHONE_NUMBER** outside of code as **PidTagBusiness2TelephoneNumber**, and use either **PR_BUSINESS2_TELEPHONE_NUMBER** or **PR_OFFICE2_TELEPHONE_NUMBER** in code. 
  
If you must use canonical property names in your code, you must first define them in your own header files.
  
## Canonical Property Names and Exchange Protocol Specifications

Canonical names are referenced in Microsoft Exchange Server protocol specifications that are used by Exchange Server to communicate with other Microsoft products. For more information about message object properties referenced by Exchange protocol specifications, see [[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx).
  
## See also

#### Concepts

[MAPI Property Tags](mapi-property-tags.md)
  
[MAPI Property Identifier Overview](mapi-property-identifier-overview.md)
  
[MAPI Property Type Overview](mapi-property-type-overview.md)

