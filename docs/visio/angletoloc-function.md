---
title: "ANGLETOLOC Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253217
 
localization_priority: Normal
ms.assetid: ee5e3898-bb49-57c6-0ebe-12e1fe388e55
description: "Returns a transformed angle in the destination shape's local coordinate system. Converts an angle from local coordinates in a source shape to the local coordinates in a destination shape."
---

# ANGLETOLOC Function

Returns a transformed angle in the destination shape's local coordinate system. Converts an angle from local coordinates in a source shape to the local coordinates in a destination shape. 
  
## Syntax

ANGLETOLOC(** *srcAngle* **, ** *srcRef* **, ** *dstRef* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _srcAngle_ <br/> |Required  <br/> |**Numeric** <br/> |An angle in the source coordinate system.  <br/> |
| _srcRef_ <br/> |Required  <br/> |**String** <br/> | A reference to a cell in the source object, such as a shape, group, page, and so on.  <br/> |
| _dstRef_ <br/> |Required  <br/> |**String** <br/> |A reference to a cell in the destination object, such as a shape, group, page, and so on.  <br/> |
   
## Remarks

You can use the ANGLETOLOC function to set local angle cells in a shape in terms of an angle from another coordinate space.
  
This function works even when the source and destination shapes are within groups. It also adjusts for rotation and flips in the intermediate transformation.
  
The source and destination coordinates must be on the same page.
  

