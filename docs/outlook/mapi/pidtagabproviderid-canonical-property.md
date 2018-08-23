---
title: "PidTagAbProviderId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagAbProviderId
api_type:
- HeaderDef
ms.assetid: 23cfd1d0-8e9d-4508-93dd-a88c0ef77c51
description: "Last modified: March 09, 2015"
---

# PidTagAbProviderId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an address book provider's [MAPIUID](mapiuid.md) structure. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_AB_PROVIDER_ID  <br/> |
|Identifier:  <br/> |0x3615  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

The **MAPIUID** structure identifies which address book provider supplies this particular container in the container hierarchy. The value is unique to each provider. 
  
An address book provider can provide more than one identifier. For example, a provider that supplies two different containers can publish in **PR_AB_PROVIDER_ID** unique identifiers for each container. 
  
 **PR_AB_PROVIDER_ID** is analogous to the **PR_MDB_PROVIDER** ([PidTagStoreProvider](pidtagstoreprovider-canonical-property.md)) property for message stores. Client applications can use **PR_AB_PROVIDER_ID** to find related rows in an address book hierarchy table. 
  
## Related resources

### Header files

Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPIUID](mapiuid.md)
  
[PidTagStoreProvider Canonical Property](pidtagstoreprovider-canonical-property.md)


[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

