---
title: "SplineStart Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm3055
 
localization_priority: Normal
ms.assetid: 8e327e00-0844-efa4-900b-6954d3b009bb
description: "Contains x - and y -coordinates for a spline's second control point, its second knot, its first knot, the last knot, and the degree of the spline."
---

# SplineStart Row (Geometry Section)

Contains  *x*  - and  *y*  -coordinates for a spline's second control point, its second knot, its first knot, the last knot, and the degree of the spline. 
  
A SplineStart row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The  *x*  -coordinate of a spline's second control point.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |The  *y*  -coordinate of a spline's second control point.  <br/> |
|[A](a-cell-geometry-section.md) <br/> |The second knot of the spline.  <br/> |
|[B](b-cell-geometry-section.md) <br/> |The first knot of a spline.  <br/> |
|[C](c-cell-geometry-section.md) <br/> |The last knot of a spline.  <br/> |
|[D](d-cell-geometry-section.md) <br/> |The degree of a spline (an integer from 1 to 25).  <br/> |
   
## Remarks

Visio displays the definition of a spline in a Geometry section that contains a SplineStart row followed by one or more SplineKnot rows. The SplineStart row must be preceded by another kind of row, such as a MoveTo row, to indicate the first control point of the spline. The preceding row can be a LineTo, ArcTo, NURBSTo, PolylineTo, or EllipticalArcTo row if the spline follows a segment of that type.
  

