---
title: "PidTagXCoordinate Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagXCoordinate
api_type:
- COM
ms.assetid: 030d5c21-ab02-4047-bf2d-9a402a1e9102
description: "Last modified: March 09, 2015"
---

# PidTagXCoordinate Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the x coordinate of the starting position (the upper-left corner) of a dialog box control, in standard Windows dialog units.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_XPOS  <br/> |
|Identifier:  <br/> |0x3F05  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI display table  <br/> |
   
## Remarks

This property, **PR_YPOS** ([PidTagYCoordinate](pidtagycoordinate-canonical-property.md)), **PR_DELTAX** ([PidTagDeltaX](pidtagdeltax-canonical-property.md)), and **PR_DELTAY** ([PidTagDeltaY](pidtagdeltay-canonical-property.md)) properties position and size the dialog box control.
  
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

