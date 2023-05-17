---
title: "PidTagDistributionListExpansionHistory Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDistributionListExpansionHistory
api_type:
- HeaderDef
ms.assetid: fc1e0162-d655-4761-92e7-b469579c270b
description: "Contains a history showing how a distribution list has been expanded during message transmission."
---

# PidTagDistributionListExpansionHistory Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a history showing how a distribution list has been expanded during message transmission. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_DL_EXPANSION_HISTORY  <br/> |
|Identifier:  <br/> |0x0013  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property is available to receiving client applications if the transport provider has set it. It is also available to the sending client if the message content is returned with a report. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagDistributionListExpansionProhibited Canonical Property](pidtagdistributionlistexpansionprohibited-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

