---
title: "PidTagYCoordinate Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagYCoordinate
api_type:
- COM
ms.assetid: f176308d-efb9-460c-8379-8a12d4f8e017
description: "Contains the y coordinate of the starting position (the upper-left corner) of a dialog box control, in standard Windows dialog units."
---

# PidTagYCoordinate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the y coordinate of the starting position (the upper-left corner) of a dialog box control, in standard Windows dialog units.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_YPOS  <br/> |
|Identifier:  <br/> |0x3F06  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI display table  <br/> |
   
## Remarks

The **PR_XPOS** ([PidTagXCoordinate](pidtagxcoordinate-canonical-property.md)), this property, **PR_DELTAX** ([PidTagDeltaX](pidtagdeltax-canonical-property.md)), and **PR_DELTAY** ([PidTagDeltaY](pidtagdeltay-canonical-property.md)) properties position and size the control.
  
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

