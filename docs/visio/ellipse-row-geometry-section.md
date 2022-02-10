---
title: "Ellipse Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm3010
 
ms.localizationpriority: medium
ms.assetid: 183fb303-4acb-a486-7b97-f11f7ae3978f
description: "Contains the x - and y -coordinates of the ellipse's center point and two points on the ellipse."
---

# Ellipse Row (Geometry Section)

Contains the  *x*  - and  *y*  -coordinates of the ellipse's center point and two points on the ellipse. 
  
An Ellipse row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The *x*  -coordinate of the center point. |
|[Y](y-cell-geometry-section.md) <br/> |The *y*  -coordinate of the center point. |
|[A](a-cell-geometry-section.md) <br/> |The x-coordinate of one point on the ellipse; paired with  *y*  -coordinate represented by the B cell. |
|[B](b-cell-geometry-section.md) <br/> |The *y*  -coordinate of one point on the ellipse; paired with x-coordinate represented by the A cell. |
|[C](c-cell-geometry-section.md) <br/> |The *x*  -coordinate of another point on the ellipse; paired with  *y*  -coordinate represented by the D cell. |
|[D](d-cell-geometry-section.md) <br/> |The *y*  -coordinate of another point on the ellipse; paired with  *y*  -coordinate represented by the C cell. |
   
## Remarks

A geometry section that contains an Ellipse or an InfiniteLine row should not contain any other rows.
  

