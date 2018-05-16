---
title: "PidTagLatestDeliveryTime Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagLatestDeliveryTime
api_type:
- HeaderDef
ms.assetid: 6c2e64bc-786e-4867-a504-46f4d1214337
description: "Last modified: March 09, 2015"
---

# PidTagLatestDeliveryTime Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the latest date and time when a message transfer agent (MTA) should deliver a message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_LATEST_DELIVERY_TIME  <br/> |
|Identifier:  <br/> |0x0019  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

If an MTA cannot deliver a message by the time this property specifies, it cancels the message without delivery. 
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

