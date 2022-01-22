---
title: "SplineKnot Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm3050
 
ms.localizationpriority: medium
ms.assetid: 9fbae27d-4f1b-c5f7-aacb-16f359331e83
description: "Contains x - and y -coordinates for a spline's control point and a spline's knot."
---

# SplineKnot Row (Geometry Section)

Contains  *x*  - and  *y*  -coordinates for a spline's control point and a spline's knot. 
  
A SplineKnot row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The *x*  -coordinate of a control point.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |The *y*  -coordinate of a control point.  <br/> |
|[A](a-cell-geometry-section.md) <br/> |One of the spline's knots (other than the last one or the first two).  <br/> |
   
## Remarks

Visio displays the definition of a spline in a Geometry section that contains a SplineStart row followed by one or more SplineKnot rows. The SplineStart row must be preceded by another kind of row, such as a MoveTo row, to indicate the first control point of the spline. The preceding row can be a LineTo, ArcTo, NURBSTo, PolylineTo, or EllipticalArcTo row if the spline follows a segment of that type.
  

