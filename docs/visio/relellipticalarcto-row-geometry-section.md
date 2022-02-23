---
title: "RelEllipticalArcTo Row (Geometry Section)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference 
ms.localizationpriority: medium
ms.assetid: 9b7da082-5e55-411d-b109-7fb6fa8f6e8e
description: "Contains x - and y -coordinates of an elliptical arc's endpoint relative to the shape's width and height, x - and y -coordinates of the control points on the arc relative to the shape's width and height, angle from the x -axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes."
---

# RelEllipticalArcTo Row (Geometry Section)

Contains *x* - and *y* -coordinates of an elliptical arc's endpoint relative to the shape's width and height, *x* - and *y* -coordinates of the control points on the arc relative to the shape's width and height, angle from the *x* -axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes.
  
> [!NOTE]
> A **RelEllipticalArcTo** row can only be persisted in the .vsdx, .vsdm, .vstx, .vstm, .vssx, and .vssm file formats. When a file is saved to the Visio 2003-2010 formats, the **RelEllipticalArcTo** row is converted to an [EllipticalArcTo](ellipticalarcto-row-geometry-section.md) row.
  
A **RelEllipticalArcTo** row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The *x* -coordinate of the ending vertex on an arc relative to the width of the shape. |
|[Y](y-cell-geometry-section.md) <br/> |The *y* -coordinate of the ending vertex on an arc relative to the height of the shape. |
|[A](a-cell-geometry-section.md) <br/> |The *x* -coordinate of the arc's control point relative to the shape's width; a point on the arc. The control point is best located about halfway between the beginning and ending vertices of the arc. Otherwise, the arc may grow to an extreme size in order to pass through the control point, with unpredictable results. |
|[B](b-cell-geometry-section.md) <br/> |The *y* -coordinate of an arc's control point relative to the shape's width. |
|[C](c-cell-geometry-section.md) <br/> |The angle of an arc's major axis relative to the *x* -axis of its parent. |
|[D](d-cell-geometry-section.md) <br/> |The ratio of an arc's major axis to its minor axis. Despite the usual meaning of these words, the "major" axis does not have to be greater than the "minor" axis, so this ratio does not have to be greater than 1. Setting this cell to a value less than or equal to 0 or greater than 1000 can lead to unpredictable results. |

## Remarks

Values in the **RelEllipticalArcTo** row are equivalent to values in an [EllipticalArcTo](ellipticalarcto-row-geometry-section.md) row, multiplied by the width and height of the shape. For example: a **RelEllipticalArcTo** row where the **X**, **Y**, **A**, **B**, **C**, and **D** cells have the values 1, 1, 1.5, 0.5, 15 deg, and 1.5 (respectively) can be replaced with an **EllipticalArcTo** row with the cell formulas `Width*1`, `Height*1'`, `Width*1.5`, `Height*0.5`, 15 deg, and 1.5 (respectively).
  