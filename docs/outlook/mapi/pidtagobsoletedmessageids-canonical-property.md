---
title: "PidTagObsoletedMessageIds Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagObsoletedMessageIds
api_type:
- HeaderDef
ms.assetid: bc979398-f1ad-4496-b982-428b95719369
description: "Contains the identifiers of messages that this message supersedes. The identifiers are standard search keys using the format of the PR_SEARCH_KEY property."
---

# PidTagObsoletedMessageIds Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the identifiers of messages that this message supersedes.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_OBSOLETED_IPMS  <br/> |
|Identifier:  <br/> |0x001F  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

The identifiers contained in this property are standard search keys using the format of the **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property.
  
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

