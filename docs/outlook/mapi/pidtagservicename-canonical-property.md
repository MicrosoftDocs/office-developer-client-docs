---
title: "PidTagServiceName Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceName
api_type:
- COM
ms.assetid: 9a63d647-7504-42fc-b317-6b02b89070eb
description: "Last modified: March 09, 2015"
---

# PidTagServiceName Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the name of a message service as set by the user in the MapiSvc.inf file.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_NAME, PR_SERVICE_NAME_A, PR_SERVICE_NAME_W  <br/> |
|Identifier:  <br/> |0x3D09  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

The name contained in these properties is specific to the message service. It comes from the [Services] section in MapiSvc.inf.
  
These properties appear as a column in the message service table and can be used to filter services. Because it is used to identify and filter services, the value should not be localized.
  
## Related resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

