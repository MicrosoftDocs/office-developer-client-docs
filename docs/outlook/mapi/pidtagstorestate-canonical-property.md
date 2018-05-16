---
title: "PidTagStoreState Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagStoreState
api_type:
- COM
ms.assetid: 36e49cf5-1411-42c5-9112-09958243996d
description: "Last modified: March 09, 2015"
---

# PidTagStoreState Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a flag that describes the state of the message store. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_STORE_STATE  <br/> |
|Identifier:  <br/> |0x340E  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI message store  <br/> |
   
## Remarks

This property is dynamic and can change based on user actions, unlike the **PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property. 
  
The following value can be set:
  
STORE_HAS_SEARCHES 
  
> The user has created one or more active searches in the store.
    
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCSTOR]](http://msdn.microsoft.com/library/d42ed1e0-3e77-4264-bd59-7afc583510e2%28Office.15%29.aspx)
  
> Specifies permissible operations for the core message store objects.
    
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

