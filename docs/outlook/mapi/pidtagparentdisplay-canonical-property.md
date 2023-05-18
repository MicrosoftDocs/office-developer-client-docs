---
title: "PidTagParentDisplay Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagParentDisplay
api_type:
- COM
ms.assetid: 6a36f4fb-17c0-4271-87d4-a92895f35f23
description: "Contains the display name of the folder where a message was found during a search. These properties only appear in the contents table of a search-results folder."
---

# PidTagParentDisplay Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the display name of the folder where a message was found during a search.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_PARENT_DISPLAY, PR_PARENT_DISPLAY_A, PR_PARENT_DISPLAY_W  <br/> |
|Identifier:  <br/> |0x0E05  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI non-transmittable  <br/> |
   
## Remarks

These properties is not on any object. They can only appear in the contents table of a search-results folder.
  
These properties and **PR_PARENT_ENTRYID** ([PidTagParentEntryId](pidtagparententryid-canonical-property.md)) properties are not related to each other. They belong to entirely different contexts.
  
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

