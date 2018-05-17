---
title: "PidTagOwnStoreEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOwnStoreEntryId
api_type:
- COM
ms.assetid: 6a82ee90-10a1-49e0-8f3a-a2cd9f490f99
description: "Last modified: March 09, 2015"
---

# PidTagOwnStoreEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the entry identifier of a transport's tightly coupled message store.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_OWN_STORE_ENTRYID  <br/> |
|Identifier:  <br/> |0x3E06  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Message Store Properties  <br/> |
   
## Remarks

This property specifies the entry identifier for the tightly coupled store, if one exists. For example, a transport provider can specify the private folder store entry identifier so that the MAPI spooler can connect the transport provider to the store.
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

