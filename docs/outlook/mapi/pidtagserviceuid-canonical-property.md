---
title: "PidTagServiceUid Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceUid
api_type:
- COM
ms.assetid: 9d99a3b6-d0b4-4e8a-8f08-f46fdeb6b3e7
description: "Last modified: March 09, 2015"
---

# PidTagServiceUid Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the [MAPIUID](mapiuid.md) structure for a message service. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_UID  <br/> |
|Identifier:  <br/> |0x3D0C  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

This property is computed by MAPI on profile section objects. MAPI uses it to group all the providers that belong to the same message service. This property is supplied as a parameter to most of the [IMsgServiceAdmin](imsgserviceadminiunknown.md) methods. It must not appear in Mapisvc.inf. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

