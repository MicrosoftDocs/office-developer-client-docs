---
title: "PidTagMappingSignature Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMappingSignature
api_type:
- HeaderDef
ms.assetid: a5e9f807-12a9-4bc9-a6a5-17579e747ffa
description: "Last modified: March 09, 2015"
---

# PidTagMappingSignature Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the mapping signature for named properties of a particular MAPI object. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MAPPING_SIGNATURE  <br/> |
|Identifier:  <br/> |0x0FF8  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

It is recommended that objects having named properties expose this property. A client application should check the **PR_MAPPING_SIGNATURE** property of both objects when copying named properties from one object to another. Use of this property can minimize translating between copied properties' names and identifiers. 
  
If this property does not exist for a given MAPI object, then the object has its own unique mapping of names and identifiers. In this case the client must call the [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) method on the source object and then the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method on the destination object. 
  
When two objects have the same **PR_MAPPING_SIGNATURE** value, the client does not need to translate name to identifier and identifier to name. The client can simply call the [IMAPIProp::GetProps](imapiprop-getprops.md) method on the source and then the [IMAPIProp::SetProps](imapiprop-setprops.md) method on the destination. This is convenient for clients that perform custom copying of named properties, and for providers implementing the [IMAPIProp::CopyTo](imapiprop-copyto.md) and [IMAPIProp::CopyProps](imapiprop-copyprops.md) methods. 
  
For more information on named properties and mapping of names and identifiers, see [MAPI Named Properties](mapi-named-properties.md). 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPINAMEID](mapinameid.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

