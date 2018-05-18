---
title: "PidTagOriginalDisplayName Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginalDisplayName
api_type:
- COM
ms.assetid: 176245d9-724d-44f1-b7a3-eddf652533b2
description: "Last modified: March 09, 2015"
---

# PidTagOriginalDisplayName Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the original display name for an entry copied from an address book to a personal address book or other writable address book.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_DISPLAY_NAME, PR_ORIGINAL_DISPLAY_NAME_A, PR_ORIGINAL_DISPLAY_NAME_W  <br/> |
|Identifier:  <br/> |0x3A13  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties contain information about the original source of a copied entry.
  
For a nonread report, these properties contain a copy of the display name of the original message recipient for which the report is generated. When the original recipient is part of a distribution list, the display name of the distribution list is preserved for the report.
  
A client application can use these properties to prevent alteration or "spoofing" of entries, by giving an unaltered copy of the display name to compare.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagTransmittableDisplayName Canonical Property](pidtagtransmittabledisplayname-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

