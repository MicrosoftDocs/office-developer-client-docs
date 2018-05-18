---
title: "PidTagMiniIcon Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMiniIcon
api_type:
- HeaderDef
ms.assetid: a436b590-63f3-413c-a9c2-7664567e0ff0
description: "Last modified: March 09, 2015"
---

# PidTagMiniIcon Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a bitmap of a half-size icon for a form.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MINI_ICON  <br/> |
|Identifier:  <br/> |0x0FFC  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property contains a 32 × 32 pixel image of an icon, the same as the contents of a .ICO file, but only the upper left 16 × 16 pixels are considered significant. This property is normally copied from the .ICO file specified in the SmallIcon line of the appropriate [Description] section of the form configuration file.
  
 **Note** Some platforms do not support 16 × 16 pixel icons. The 32 × 32 format of this property is usable in such a case but client applications should be aware of display inconsistencies. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagIcon Canonical Property](pidtagicon-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

