---
title: "RelCubBezTo Row (Geometry Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 77777dd4-5a2c-4048-9ea4-9bd876862963
description: "Contains the x - and y -coordinates of the endpoint of a cubic Bézier curve relative to the shape's width and height, the x - and y -coordinates of the control point of the beginning of the curve relative shape's width and height, and the x - and y -coordinates of the control point of the ending of the curve relative shape's width and height."
---

# RelCubBezTo Row (Geometry Section)

Contains the  *x*  - and  *y*  -coordinates of the endpoint of a cubic Bézier curve relative to the shape's width and height, the  *x*  - and  *y*  -coordinates of the control point of the beginning of the curve relative shape's width and height, and the  *x*  - and  *y*  -coordinates of the control point of the ending of the curve relative shape's width and height. 
  
> [!NOTE]
> A **RelCubBezTo** row can only be persisted in the .vsdx, .vsdm, .vstx, .vstm, .vssx, and .vssm file formats. When a file is saved to the Visio 2003-2010 formats, the **RelCubBezTo** row is converted to a [NURBSTo](nurbsto-row-geometry-section.md) row. 
  
A **RelCubBezTo** row contains the following cells. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The *x*  -coordinate of the ending vertex of a cubic Bézier curve relative to the width of the shape. |
|[Y](y-cell-geometry-section.md) <br/> |The *y*  -coordinate of the ending vertex of a cubic Bézier curve relative to the height of the shape. |
|[A](a-cell-geometry-section.md) <br/> |The *x*  -coordinate of the curve's beginning control point relative to the shape's width; a point on the arc. The control point is best located between the beginning and ending vertices of the arc. |
|[B](b-cell-geometry-section.md) <br/> |The *y*  -coordinate of a curve's beginning control point relative to the shape's height. |
|[C](c-cell-geometry-section.md) <br/> |The *x*  -coordinate of the curve's ending control point relative to the shape's width; a point on the arc. The control point is best located between the beginning control point and ending vertices of the arc. |
|[D](d-cell-geometry-section.md) <br/> |The *y*  -coordinate of a curve's ending control point relative to the shape's height. |
   

