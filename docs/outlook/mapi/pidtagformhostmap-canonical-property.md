---
title: "PidTagFormHostMap Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFormHostMap
api_type:
- HeaderDef
ms.assetid: 92742747-cce0-4c54-9ece-1fcf652ac498
description: "Last modified: March 09, 2015"
---

# PidTagFormHostMap Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a host map of available forms. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FORM_HOST_MAP  <br/> |
|Identifier:  <br/> |0x3306  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

A client application should update this property, along with the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property, when changing the underlying structure in the **IMAPIFormProp** interface. 
  
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

