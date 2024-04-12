---
title: "PidTagContentReturnRequested Canonical Property"
description: Outlines the PidTagContentReturnRequested canonical property, which contains TRUE if a message should be returned with a nondelivery report.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagContentReturnRequested
api_type:
- HeaderDef
ms.assetid: f86f7c59-42ab-4ac0-80fe-c985103e6bd6
---

# PidTagContentReturnRequested Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE if a message should be returned with a nondelivery report. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTENT_RETURN_REQUESTED  <br/> |
|Identifier:  <br/> |0x000A  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Report  <br/> |
   
## Remarks

If this property is not set, MAPI treats it as having a TRUE value. 
  
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

