---
title: "PidTagResourceType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagResourceType
api_type:
- COM
ms.assetid: 48b634d7-deea-422b-8944-a8d929d83838
description: "Contains a value that indicates the service provider type for Outlook 2013 or Outlook 2016."
---

# PidTagResourceType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a value that indicates the service provider type.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RESOURCE_TYPE  <br/> |
|Identifier:  <br/> |0x3E03  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

This property can have exactly one of the following values:
  
MAPI_AB 
  
> Address book
    
MAPI_AB_PROVIDER 
  
> Address book provider
    
MAPI_HOOK_PROVIDER 
  
> Spooler hook provider
    
MAPI_PROFILE_PROVIDER 
  
> Profile provider
    
MAPI_SPOOLER 
  
> Message spooler
    
MAPI_STORE_PROVIDER 
  
> Message store provider
    
MAPI_SUBSYSTEM 
  
> Internal MAPI subsystem
    
MAPI_TRANSPORT_PROVIDER 
  
> Transport provider
    
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

