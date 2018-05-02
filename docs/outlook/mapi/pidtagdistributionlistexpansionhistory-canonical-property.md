---
title: "PidTagDistributionListExpansionHistory Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagDistributionListExpansionHistory
api_type:
- HeaderDef
ms.assetid: fc1e0162-d655-4761-92e7-b469579c270b
description: "Last modified: March 09, 2015"
---

# PidTagDistributionListExpansionHistory Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains a history showing how a distribution list has been expanded during message transmission. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DL_EXPANSION_HISTORY  <br/> |
|Identifier:  <br/> |0x0013  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property is available to receiving client applications if the transport provider has set it. It is also available to the sending client if the message content is returned with a report. 
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Reference

[PidTagDistributionListExpansionProhibited Canonical Property](pidtagdistributionlistexpansionprohibited-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

