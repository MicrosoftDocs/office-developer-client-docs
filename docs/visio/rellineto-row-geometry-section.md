---
title: "RelLineTo Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a900e174-d26a-4314-ae4f-d89e186350ce
description: "Contains x -and y -coordinates of the ending vertex of a straight line segment relative to a shape's width and height."
---

# RelLineTo Row (Geometry Section)

Contains  *x*  -and  *y*  -coordinates of the ending vertex of a straight line segment relative to a shape's width and height. 
  
> [!NOTE]
> A **RelLineTo** row can only be persisted in the .vsdx, .vsdm, .vstx, .vstm, .vssx, and .vssm file formats. When a file is saved to the Visio 2003-2010 formats, the **RelLineTo** row is converted to a [LineTo](lineto-row-geometry-section.md) row. 
  
A **RelLineTo** row contains the following cells. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The  *x*  -coordinate of the ending vertex of a straight line segment relative to the shape's width.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |The  *y*  -coordinate of the ending vertex of a straight line segment relative to the shape's height.  <br/> |
   
## Remarks

Values in the **RelLineTo** row are equivalent to values in a [LineTo](lineto-row-geometry-section.md) row that are multiplied by the width and height of the shape. For example: a **RelLineTo** row where the value of the **X** cell is "0" and the value of the **Y** cell is "0.5" can be replaced with **LineTo** row where the value of the **X** cell is the formula "Width*0" and the **Y** cell is the formula "Height*0.5." 
  

