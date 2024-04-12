---
title: "PidTagProviderItemId Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagProviderItemId
api_type:
- COM
ms.assetid: fadbf1af-32c2-43ea-8475-15b31b2a9e68
description: "Specifies an identifier for a folder or an item in a store. Store providers use this property to identify search results returned from a search engine."
---

# PidTagProviderItemId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies an identifier for a folder or an item in a store.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_PROVIDER_ITEMID  <br/> |
|Identifier:  <br/> |0x0EA3  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MapiNonTransmittable  <br/> |
   
## Remarks

Store providers can specify a value for this property for a folder or an item, but should keep the value the same between sessions. Store providers use this property to identify search results returned from a search engine.
  
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

