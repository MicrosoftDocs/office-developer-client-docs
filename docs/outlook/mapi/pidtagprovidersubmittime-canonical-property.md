---
title: "PidTagProviderSubmitTime Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagProviderSubmitTime
api_type:
- COM
ms.assetid: 9e5161d9-fefe-4a12-b7f7-5600f1d2e95b
description: "Last modified: March 09, 2015"
---

# PidTagProviderSubmitTime Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the date and time a transport provider passed a message to its underlying messaging system.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PROVIDER_SUBMIT_TIME  <br/> |
|Identifier:  <br/> |0x0048  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property is set by the outgoing transport provider at the time a message is sent.
  
This property corresponds to an X.400 submission envelope per-message attribute. 
  
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

