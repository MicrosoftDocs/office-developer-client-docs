---
title: "RelMoveTo Row (Geometry Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 04a0ba9f-48dd-488f-9c87-3890a12adf89
description: "Contains the x - and y -coordinates of the first vertex of a shape or the x - and y -coordinates of the first vertex after a break in a path, relative to the height and width of the shape."
---

# RelMoveTo Row (Geometry Section)

Contains the  *x*  - and  *y*  -coordinates of the first vertex of a shape or the  *x*  - and  *y*  -coordinates of the first vertex after a break in a path, relative to the height and width of the shape. 
  
> [!NOTE]
> A **RelMoveTo** row can only be persisted in the .vsdx, .vsdm, .vstx, .vstm, .vssx, and .vssm file formats. When a file is saved to the Visio 2003-2010 formats, the **RelMoveTo** row is converted to a [MoveTo](moveto-row-geometry-section.md) row. 
  
A **RelMoveTo** row contains the following cells. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |If the **RelMoveTo** row is the first row in the section, the X cell represents the  *x*  -coordinate of the first vertex of a shape relative to the width of the shape. If the **RelMoveTo** row appears between two rows, the X cell represents the  *x*  -coordinate of the first vertex after the break in the path. |
|[Y](y-cell-geometry-section.md) <br/> |If the **RelMoveTo** row is the first row in the section, the Y cell represents the  *y*  -coordinate of the first vertex of a shape. If the **RelMoveTo** row appears between two rows, the Y cell represents the  *y*  -coordinate of the first vertex after the break in the path. |
   
## Remarks

Values in the **RelMoveTo** row are equivalent to values in a [MoveTo](moveto-row-geometry-section.md) row that are multiplied by the width and height of the shape. For example: a **RelMoveTo** row where the value of the **X** cell is "0" and the value of the **Y** cell is "0.5" could be replaced with **MoveTo** row where the value of the **X** cell is the formula "Width*0" and the **Y** cell is the formula "Height*0.5." 
  
The **RelMoveTo** row contains the  *x*  - and  *y*  -coordinates of the first vertex for the shape if the MoveTo row is the first row in the section. Usually this is the first vertex placed when the shape was drawn, and it does not necessarily correspond to the begin point of a 1-D shape. 
  
A **Geometry** section must begin with a **MoveTo** or a **RelMoveTo** row, but you can also use the **RelMoveTo** row and **MoveTo** row to represent a gap in the stroking of a shape's path relative to the shape's width and height. However, when the path is used to define the boundary of a filled region, this gap is interpreted as a straight line segment. To insert such a gap, insert a row between two rows and change the row type to **RelMoveTo**. If the **RelMoveTo** row is between two rows, it contains the  *x*  - and  *y*  -coordinates of the first vertex of the line after the break in the shape's path. 
  

