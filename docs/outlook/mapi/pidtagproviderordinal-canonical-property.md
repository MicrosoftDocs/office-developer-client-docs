---
title: "PidTagProviderOrdinal Canonical Property"
description: Outlines the PidTagProviderOrdinal canonical property, which contains the zero-based index of a service provider's position in the provider table.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagProviderOrdinal
api_type:
- COM
ms.assetid: d062b54d-7c32-4369-ab69-f7193773a1c0
---

# PidTagProviderOrdinal Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the zero-based index of a service provider's position in the provider table.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_PROVIDER_ORDINAL  <br/> |
|Identifier:  <br/> |0x300D  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

This property is computed by MAPI.
  
Obtain the provider table by calling the [IMsgServiceAdmin::GetProviderTable](imsgserviceadmin-getprovidertable.md) method. Sort the provider table on this property to display the transport order. 
  
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

