---
title: "PidTagImplicitConversionProhibited Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagImplicitConversionProhibited
api_type:
- HeaderDef
ms.assetid: c6cb5a86-0105-4743-9f8e-b832e898da52
description: "Last modified: March 09, 2015"
---

# PidTagImplicitConversionProhibited Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if a message transfer agent (MTA) is prohibited from making implicit message text conversions.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_IMPLICIT_CONVERSION_PROHIBITED  <br/> |
|Identifier:  <br/> |0x0016  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

If this property is TRUE, the messaging system must not perform any content conversion on the message unless it is explicitly requested on a per-recipient basis with the **PR_EXPLICIT_CONVERSION** ( [PidTagExplicitConversion](pidtagexplicitconversion-canonical-property.md)) property.
  
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

