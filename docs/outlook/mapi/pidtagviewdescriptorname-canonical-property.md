---
title: "PidTagViewDescriptorName Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagViewDescriptorName
api_type:
- COM
ms.assetid: 1e689ee4-9e89-4328-beb9-05c80a6544a0
description: "Last modified: March 09, 2015"
---

# PidTagViewDescriptorName Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the name of a view descriptor.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_VD_NAME, PR_VD_NAME_A, PR_VD_NAME_W  <br/> |
|Identifier:  <br/> |0x7006  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Message class-defined transmittable  <br/> |
   
## Remarks

These properties must be set to a non-empty string for a Folder Associate Information (FAI) message that contains view definitions.
  
## Related resources

### Protocol specifications

[[MS-OXOCFG]](http://msdn.microsoft.com/library/7d466dd5-c156-4da9-9a01-75c78e7e1a67%28Office.15%29.aspx)
  
> Specifies the location and properties of client and server configuration data, such as shared category lists and working hours.
    
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

