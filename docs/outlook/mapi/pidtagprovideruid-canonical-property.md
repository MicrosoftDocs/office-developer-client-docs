---
title: "PidTagProviderUid Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagProviderUid
api_type:
- COM
ms.assetid: 993f5bca-58a6-455d-8a25-6e08b441ad31
description: "Last modified: March 09, 2015"
---

# PidTagProviderUid Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a **MAPIUID** structure of the service provider that is handling a message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PROVIDER_UID  <br/> |
|Identifier:  <br/> |0x300C  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

This property is computed by all service providers. It contains a [MAPIUID](mapiuid.md) structure associated with, and usually hard-coded by, the provider. It is typically used by a client application that is interested in only the address book containers supplied by a particular provider. 
  
This property appears only as a column entry in the provider table.
  
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

