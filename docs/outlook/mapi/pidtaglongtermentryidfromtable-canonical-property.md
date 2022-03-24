---
title: "PidTagLongTermEntryIdFromTable Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagLongTermEntryIdFromTable
api_type:
- HeaderDef
ms.assetid: d9457fea-4b1e-4cf6-9c4b-14c98fbec2a1
description: "Obtains the long- term entry identifier of an item. This property can be used to get the entry identifier of an item as a long-term entry identifier."
---

# PidTagLongTermEntryIdFromTable Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Obtains the long- term entry identifier of an item.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_LONGTERM_ENTRYID_FROM_TABLE  <br/> |
|Identifier:  <br/> |0x6670  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Table Properties  <br/> |
   
## Remarks

This property can be used in a contents table to get the entry identifier of an item as a long-term entry identifier instead of a short-term entry identifier. For information about long-term and short-term identifiers, see **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)).
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagEntryId Canonical Property](pidtagentryid-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

