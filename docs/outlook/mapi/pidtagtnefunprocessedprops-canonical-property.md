---
title: "PidTagTnefUnprocessedProps Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagTnefUnprocessedProps
api_type:
- COM
ms.assetid: df9cd614-1198-44a2-9bf5-36c57179a9a9
description: "Last modified: March 09, 2015"
---

# PidTagTnefUnprocessedProps Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Serializes properties when filtering Transport Neutral Encapsulation Format (TNEF).
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_TNEF_UNPROCESSED_PROPS  <br/> |
|Identifier:  <br/> |0x0E9C  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI non-transmittable  <br/> |
   
## Remarks

Used by Microsoft Outlook and Outlook Web Access (OWA) for saving the original TNEF in cases where the TNEF contains named properties that cannot be created in the store.
  
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

