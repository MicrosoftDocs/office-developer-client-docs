---
title: "ArcTo Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253229
 
localization_priority: Normal
ms.assetid: 612b605d-a703-b08f-2e8e-7bc1624b5370
description: "Contains the x - and y -coordinates and bow of a circular arc."
---

# ArcTo Row (Geometry Section)

Contains the  *x*  - and  *y*  -coordinates and bow of a circular arc. 
  
An ArcTo row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The  *x*  -coordinate of the ending vertex of an arc.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |The  *y*  -coordinate of the ending vertex of an arc.  <br/> |
|[A](a-cell-geometry-section.md) <br/> |The distance from the arc's midpoint to the midpoint of its chord.  <br/> |
   
## Remarks

Arcs drawn in Visio are elliptical arcs, even if they are based on a circle. By default, drawn arcs are represented by an EllipticalArcTo row in a ShapeSheet window. To show an ArcTo row in a ShapeSheet window, you must draw an arc, and then change the EllipticalArcTo row type to an ArcTo row type; in effect you are changing an elliptical arc to a circular arc.
  
To change a row type, right-click a row, and then click **Change Row Type** on the shortcut menu. 
  

