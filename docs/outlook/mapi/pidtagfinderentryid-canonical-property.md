---
title: "PidTagFinderEntryId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagFinderEntryId
api_type:
- HeaderDef
ms.assetid: a3895f90-7561-4b41-92af-ecc8614e4211
description: "Contains the entry identifier for the folder where search results are typically created. This identifier has the same format as the ENTRYID structure."
---

# PidTagFinderEntryId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the entry identifier for the folder where search results are typically created.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_FINDER_ENTRYID  <br/> |
|Identifier:  <br/> |0x35E7  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI message store  <br/> |
   
## Remarks

The entry identifier contained in this property has the same format as the [ENTRYID](entryid.md) structure. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

