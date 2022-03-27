---
title: "PidTagResourcePath Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagResourcePath
api_type:
- COM
ms.assetid: ac49538e-6ee8-4ab4-9d79-88a83c7d0149
description: "Contains a path to the service provider's server. The definition of these properties is provider specific."
---

# PidTagResourcePath Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a path to the service provider's server.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RESOURCE_PATH, PR_RESOURCE_PATH_A, PR_RESOURCE_PATH_W  <br/> |
|Identifier:  <br/> |0x3E07  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

The path contained in these properties represents the suggested path where the user can find resources. The definition of these properties is provider specific. For example, a scheduling application uses these properties to specify the suggested location for its scheduling application files.
  
The messaging user profile furnishes these properties as a convenience so that a client application does not have to prompt the messaging user for a network path or network drive letter.
  
MAPI works only with filenames in the American National Standards Institute (ANSI) character set. Applications that use filenames in an original equipment manufacturer (OEM) character set must convert them to ANSI before calling MAPI.
  
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

