---
title: "PidTagCorrelate Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagCorrelate
api_type:
- HeaderDef
ms.assetid: be34993e-ffcc-47f5-b2d4-95ffa707bc5c
description: "Last modified: March 09, 2015"
---

# PidTagCorrelate Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if the sender of a message requests the correlation feature of the messaging system.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CORRELATE  <br/> |
|Identifier:  <br/> |0x0E0C  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

This property is used to request the correlation of incoming reports with the original sent message. When a transport provider encounters a submitted message with **PR_CORRELATE** set to TRUE, it sets the **PR_CORRELATE_MTSID** ([PidTagCorrelateMtsid](pidtagcorrelatemtsid-canonical-property.md)) property to the message transfer system (MTS) identifier for that message.
  
 **PR_CORRELATE** should be used with messaging systems that support correlation by MTS identifier, such as X.400. 
  
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

