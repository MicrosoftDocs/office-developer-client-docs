---
title: "ANGLETOPAR Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253218
 
ms.localizationpriority: medium
ms.assetid: 4d87313a-c09a-582c-04f4-d95800e3e9f2
description: "Returns a transformed angle in the destination shape's parent coordinate system. Converts an angle from local coordinates in a source shape to the parent coordinates in a destination shape."
---

# ANGLETOPAR Function

Returns a transformed angle in the destination shape's parent coordinate system. Converts an angle from local coordinates in a source shape to the parent coordinates in a destination shape. 
  
## Syntax

ANGLETOPAR(***srcAngle***, ***srcRef***, ***dstRef*** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _srcAngle_ <br/> |Required  <br/> |**Numeric** <br/> |An angle in the source coordinate system. |
| _srcRef_ <br/> |Required  <br/> |**String** <br/> | A reference to a cell in the source object, such as a shape, group, page, and so on. |
| _dstRef_ <br/> |Required  <br/> |**String** <br/> |A reference to a cell in the destination object, such as a shape, group, page, and so on. |
   
## Remarks

This function works even when the source and destination shapes are within groups. It also adjusts for rotation and flips in the intermediate transformation.
  
The source and destination coordinates must be on the same page.
  
If the destination is a page, which has no parent, the result is expressed in page's local coordinates.
  

