---
title: "PidTagAcknowledgementMode Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAcknowledgementMode
api_type:
- HeaderDef
ms.assetid: 23329ca3-89f9-4e5a-9c8a-6262f2a2d26f
description: "Last modified: March 09, 2015"
---

# PidTagAcknowledgementMode Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the identifier of the mode for message acknowledgment.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ACKNOWLEDGEMENT_MODE  <br/> |
|Identifier:  <br/> |0x0001  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

This property can have exactly one of the following values:
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Manual acknowledgment.  <br/> |
|1  <br/> |Automatic acknowledgment.  <br/> |
   
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

