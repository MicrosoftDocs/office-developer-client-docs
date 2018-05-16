---
title: "PidTagDetailsTable Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagDetailsTable
api_type:
- HeaderDef
ms.assetid: 7a0ccad3-f497-4871-b733-771e6cb8ef6a
description: "Last modified: March 09, 2015"
---

# PidTagDetailsTable Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an embedded display table object.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DETAILS_TABLE  <br/> |
|Identifier:  <br/> |0x3605  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |MAPI container  <br/> |
   
## Remarks

Passing this property to the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method for the object returns an [IMAPITable](imapitableiunknown.md) interface that allows creation of the display table. MAPI uses this table to display property sheets for an address book object in response to an [IAddrBook::Details](iaddrbook-details.md) call. 
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Reference

[PidTagCreateTemplates Canonical Property](pidtagcreatetemplates-canonical-property.md)
  
[PidTagSearch Canonical Property](pidtagsearch-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

