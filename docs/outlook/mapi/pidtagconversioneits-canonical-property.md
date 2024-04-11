---
title: "PidTagConversionEits Canonical Property"
description: Outlines the PidTagConversionEits canonical property, which contains the encoded information types (EITs).
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagConversionEits
api_type:
- HeaderDef
ms.assetid: f75ea086-9d65-4396-a2e3-1751351e56d3
---

# PidTagConversionEits Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the encoded information types (EITs) that are applied to a message in transit to describe conversions.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONVERSION_EITS  <br/> |
|Identifier:  <br/> |0x000C  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

X.400 environments use this property for both non-delivery and delivery reports.
  
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

