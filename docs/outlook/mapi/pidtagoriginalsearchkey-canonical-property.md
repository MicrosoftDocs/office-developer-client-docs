---
title: "PidTagOriginalSearchKey Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginalSearchKey
api_type:
- COM
ms.assetid: ac5eb91d-31c9-459b-bb22-f4ccfc92d1db
description: "Contains the original search key for an entry copied from an address book to a personal address book or other writeable address book."
---

# PidTagOriginalSearchKey Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the original search key for an entry copied from an address book to a personal address book or other writeable address book.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_SEARCH_KEY  <br/> |
|Identifier:  <br/> |0x3A14  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property is one of the properties that contain information about the original source of a copied entry.
  
For a nonread report, this property contains a copy of the search key of the original message recipient for which the report is generated. When the original recipient is part of a distribution list, the search key of the distribution list is preserved for the report.
  
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



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

