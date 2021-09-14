---
title: "EllipticalArcTo Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm3015
 
ms.localizationpriority: medium
ms.assetid: 7ceb30a8-1d05-feff-35d8-08a198784a27
description: "Contains x - and y -coordinates of an elliptical arc's endpoint, x - and y -coordinates of the control points on the arc, angle from the x -axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes."
---

# EllipticalArcTo Row (Geometry Section)

Contains  *x*  - and  *y*  -coordinates of an elliptical arc's endpoint,  *x*  - and  *y*  -coordinates of the control points on the arc, angle from the  *x*  -axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes. 
  
An EllipticalArcTo row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The  *x*  -coordinate of the ending vertex on an arc.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |The  *y*  -coordinate of the ending vertex on an arc.  <br/> |
|[A](a-cell-geometry-section.md) <br/> |The  *x*  -coordinate of the arc's control point; a point on the arc. The control point is best located about halfway between the beginning and ending vertices of the arc. Otherwise, the arc may grow to an extreme size in order to pass through the control point, with unpredictable results.  <br/> |
|[B](b-cell-geometry-section.md) <br/> |The  *y*  -coordinate of an arc's control point.  <br/> |
|[C](c-cell-geometry-section.md) <br/> |The angle of an arc's major axis relative to the  *x*  -axis of its parent.  <br/> |
|[D](d-cell-geometry-section.md) <br/> |The ratio of an arc's major axis to its minor axis. Despite the usual meaning of these words, the "major" axis does not have to be greater than the "minor" axis, so this ratio does not have to be greater than 1. Setting this cell to a value less than or equal to 0 or greater than 1000 can lead to unpredictable results.  <br/> |
   

