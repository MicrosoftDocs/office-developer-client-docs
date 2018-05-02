---
title: "MoveTo Row (Geometry Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm3030
 
localization_priority: Normal
ms.assetid: c5b20257-676c-279d-f730-1b6fbbe98305
description: "Contains the x - and y -coordinates of the first vertex of a shape, or represents the x - and y -coordinates of the first vertex after a break in a path."
---

# MoveTo Row (Geometry Section)

Contains the  *x*  - and  *y*  -coordinates of the first vertex of a shape, or represents the  *x*  - and  *y*  -coordinates of the first vertex after a break in a path. 
  
A **MoveTo** row contains the following cells. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |If the **MoveTo** row is the first row in the section, the X cell represents the  *x*  -coordinate of the first vertex of a shape. If the **MoveTo** row appears between two rows, the X cell represents the  *x*  -coordinate of the first vertex after the break in the path.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |If the **MoveTo** row is the first row in the section, the Y cell represents the  *y*  -coordinate of the first vertex of a shape. If the **MoveTo** row appears between two rows, the Y cell represents the  *y*  -coordinate of the first vertex after the break in the path.  <br/> |
   
## Remarks

The **MoveTo** row contains the  *x*  - and  *y*  -coordinates of the first vertex for the shape if the **MoveTo** row is the first row in the section. Usually this is the first vertex placed when the shape was drawn, and it does not necessarily correspond to the begin point of a 1-D shape. 
  
A geometry section must begin with either a **RelMoveTo** or a **MoveTo** row, but you can also use the **MoveTo** and **RelMoveTo** rows to represent a gap in the stroking of a shape's path. However, when the path is used to define the boundary of a filled region, this gap is interpreted as a straight line segment. To insert such a gap, insert a row between two rows and change the row type to **MoveTo**. If the **MoveTo** row is between two rows, it contains the  *x*  - and  *y*  -coordinates of the first vertex of the line after the break in the shape's path. 
  

