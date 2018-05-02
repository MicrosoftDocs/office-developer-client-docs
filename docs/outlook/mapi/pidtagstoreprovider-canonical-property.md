---
title: "PidTagStoreProvider Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagStoreProvider
api_type:
- COM
ms.assetid: 6f6cc66f-a08e-4f8e-b33a-d3674319248e
description: "Last modified: March 09, 2015"
---

# PidTagStoreProvider Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains a provider-defined [MAPIUID](mapiuid.md) structure that indicates the type of the message store. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MDB_PROVIDER  <br/> |
|Identifier:  <br/> |0x3414  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |ID properties  <br/> |
   
## Remarks

The [MAPIUID](mapiuid.md) structure identifies the type of message store. The value is computed by message store providers on message store objects and is unique to each provider. It is typically used for browsing through the message store table to find a store of the desired type, such as public folders. 
  
This property is analogous to the **PR_AB_PROVIDER_ID** ( [PidTagAbProviderId](pidtagabproviderid-canonical-property.md)) property for address books. 
  
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

