---
title: "RelQuadBezTo Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 5ae57707-5a50-43f0-8c78-516790b5034e
description: "Contains the x - and y -coordinates of the endpoint of a quadratic Bézier curve relative to the shape's width and height and the x - and y -coordinates of the control point of the curve relative shape's width and height."
---

# RelQuadBezTo Row (Geometry Section)

Contains the  *x*  - and  *y*  -coordinates of the endpoint of a quadratic Bézier curve relative to the shape's width and height and the  *x*  - and  *y*  -coordinates of the control point of the curve relative shape's width and height. 
  
> [!NOTE]
> A **RelQuadBezTo** row can only be persisted in the .vsdx, .vsdm, .vstx, .vstm, .vssx, and .vssm file formats. When a file is saved to the Visio 2003-2010 formats, the **RelQuadBezTo** row is converted to a [NURBSTo](nurbsto-row-geometry-section.md) row. 
  
A **RelQuadBezTo** row contains the following cells. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The *x*  -coordinate of the ending vertex of a quadratic Bézier curve relative to the width of the shape. |
|[Y](y-cell-geometry-section.md) <br/> |The *y*  -coordinate of the ending vertex of a quadratic Bézier curve relative to the height of the shape. |
|[A](a-cell-geometry-section.md) <br/> |The *x*  -coordinate of the curve's control point relative to the shape's width; a point on the arc. The control point is best located about halfway between the beginning and ending vertices of the arc. |
|[B](b-cell-geometry-section.md) <br/> |The *y*  -coordinate of a curve's control point relative to the shape's height. |
   

