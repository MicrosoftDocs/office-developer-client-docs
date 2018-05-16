---
title: "PidTagServiceInstallId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceInstallId
api_type:
- COM
ms.assetid: 1dd14858-2ce6-4629-a2f1-82d23cd6576b
description: "Last modified: March 09, 2015"
---

# PidTagServiceInstallId Canonical Property

  
  
**Applies to**: Outlook 
  
The component ID of the provider.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_INSTALL_ID, PR_SERVICE_INSTALL_ID_A, PR_SERVICE_INSTALL_ID_W  <br/> |
|Identifier:  <br/> |0x3D13  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

These properties may be used as the component parameter of an **MsiProvideQualifiedComponent** call to install the provider. 
  
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

