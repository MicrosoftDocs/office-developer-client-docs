---
title: "PidTagOriginallyIntendedRecipEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginallyIntendedRecipEntryId
api_type:
- COM
ms.assetid: fc288a7a-1927-484e-b860-9cc118672ed2
description: "Last modified: March 09, 2015"
---

# PidTagOriginallyIntendedRecipEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the entry identifier of the originally intended recipient of an auto-forwarded message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINALLY_INTENDED_RECIP_ENTRYID  <br/> |
|Identifier:  <br/> |0x1012  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

This property is one of the address properties for the originally intended message recipient. It must be set by the automatic agent that has forwarded the message.
  
This property corresponds to the X.400 report per-recipient attribute.
  
## Related resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

