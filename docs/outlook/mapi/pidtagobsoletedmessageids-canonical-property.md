---
title: "PidTagObsoletedMessageIds Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagObsoletedMessageIds
api_type:
- HeaderDef
ms.assetid: bc979398-f1ad-4496-b982-428b95719369
description: "Last modified: March 09, 2015"
---

# PidTagObsoletedMessageIds Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the identifiers of messages that this message supersedes.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_OBSOLETED_IPMS  <br/> |
|Identifier:  <br/> |0x001F  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

The identifiers contained in this property are standard search keys using the format of the **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property.
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

