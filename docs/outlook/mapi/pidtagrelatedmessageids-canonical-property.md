---
title: "PidTagRelatedMessageIds Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRelatedMessageIds
api_type:
- COM
ms.assetid: 51f0eb8a-0a16-4b45-9380-28caddecf955
description: "Last modified: March 09, 2015"
---

# PidTagRelatedMessageIds Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a list of identifiers for messages to which a message is related.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RELATED_IPMS  <br/> |
|Identifier:  <br/> |0x002D  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

The identifiers use the same specific construction rules as are used for the **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property.
  
## Related resources

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

