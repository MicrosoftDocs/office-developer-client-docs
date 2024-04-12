---
title: "PidTagConversionWithLossProhibited Canonical Property"
description: Outlines the PidTagConversionWithLossProhibited canonical property, which contains TRUE if an MTA is prohibited from making message text conversions.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagConversionWithLossProhibited
api_type:
- HeaderDef
ms.assetid: a18b560a-e054-45b3-946d-6504465db5b7
---

# PidTagConversionWithLossProhibited Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE if a message transfer agent (MTA) is prohibited from making message text conversions that lose information. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONVERSION_WITH_LOSS_PROHIBITED  <br/> |
|Identifier:  <br/> |0x000D  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |General configuration  <br/> |
   
## Remarks

An example of the type of conversion being prohibited is the "lossy" mapping from Unicode (two bytes per character) to a single-byte character set. 
  
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

