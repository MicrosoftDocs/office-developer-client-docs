---
title: "PidTagCorrelate Canonical Property"
description: Outlines the PidTagCorrelate canonical property, which is used to request the correlation of incoming reports with the original sent message. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagCorrelate
api_type:
- HeaderDef
ms.assetid: be34993e-ffcc-47f5-b2d4-95ffa707bc5c
---

# PidTagCorrelate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE if the sender of a message requests the correlation feature of the messaging system.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CORRELATE  <br/> |
|Identifier:  <br/> |0x0E0C  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

This property is used to request the correlation of incoming reports with the original sent message. When a transport provider encounters a submitted message with **PR_CORRELATE** set to TRUE, it sets the **PR_CORRELATE_MTSID** ([PidTagCorrelateMtsid](pidtagcorrelatemtsid-canonical-property.md)) property to the message transfer system (MTS) identifier for that message.
  
 **PR_CORRELATE** should be used with messaging systems that support correlation by MTS identifier, such as X.400. 
  
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

