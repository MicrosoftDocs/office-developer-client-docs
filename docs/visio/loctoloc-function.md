---
title: "LOCTOLOC Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251586
 
ms.localizationpriority: medium
ms.assetid: 1f09482a-0b1b-1bef-bc23-7f7793c4c65f
description: "Returns a transformed point in local coordinates in the destination coordinate system."
---

# LOCTOLOC Function

Returns a transformed point in local coordinates in the destination coordinate system.
  
## Syntax

LOCTOLOC(***srcPoint***, ***srcRef***, ***dstRef*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *srcPoint* <br/> |Required  <br/> |**String** <br/> | A point in local coordinates in the source coordinate system. |
| *srcRef* <br/> |Required  <br/> |**String** <br/> | A reference to a cell in the source object. |
| *dstRef* <br/> |Required  <br/> |**String** <br/> | A reference to a cell in the destination object. |

### Return value

String
  
## Remarks

The LOCTOLOC function converts a point from local coordinates in a source shape to local coordinates in a destination shape. You can use this function to construct a shape, for example, in terms of a point from another coordinate space. You can also use this function to transform a local point to page coordinates, or vice versa.
  
This function works even when the source and destination shapes are within groups. It also adjusts for rotation and flips in the intermediate transformation.
  
The source and destination coordinates must be on the same page.
  
## Example

The following formula converts the local pin of the shape associated with the formula to a point on the page.
  
```vb
LOCTOLOC(PNT(LocPinX, LocPinY), Width, ThePage!PageWidth)
```
