---
title: "Y Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251750
 
localization_priority: Normal
ms.assetid: a53b5787-f419-7a36-3c04-c63b3c173ac7

description: "Represents a y -coordinate on a shape in local coordinates. This table describes the Y cell based on the row in which it's located."
---

# Y Cell (Geometry Section)

Represents a  *y*  -coordinate on a shape in local coordinates. This table describes the Y cell based on the row in which it's located. 
  
|**Row**|**Description**|
|:-----|:-----|
|[NURBSTo](nurbsto-row-geometry-section.md) <br/> | If the MoveTo row is the first row in the section, the Y cell represents the  *y*  -coordinate of the first vertex of a path. If the MoveTo row appears between two rows, the Y cell represents the  *y*  -coordinate of the first vertex after the break in the path.  <br/> |
|[LineTo](lineto-row-geometry-section.md) <br/> | The  *y*  -coordinate of the ending vertex of a straight line segment.  <br/> |
|[ArcTo](arcto-row-geometry-section.md) <br/> | The  *y*  -coordinate of the ending vertex of an arc.  <br/> |
|[EllipticalArcTo](ellipticalarcto-row-geometry-section.md) <br/> | The  *y*  -coordinate of the ending vertex of an elliptical arc.  <br/> |
|[PolylineTo](polylineto-row-geometry-section.md) <br/> | The  *y*  -coordinate of the ending vertex of a polyline.  <br/> |
|[NURBSTo](nurbsto-row-geometry-section.md) <br/> | The  *y*  -coordinate of the last control point of a nonuniform rational B-spline (NURBS).  <br/> |
|[SplineStart](splinestart-row-geometry-section.md) <br/> | The  *y*  -coordinate of a spline's second control point.  <br/> |
|[SplineKnot](splineknot-row-geometry-section.md) <br/> | The  *y*  -coordinate of a control point.  <br/> |
|[InfiniteLine](infiniteline-row-geometry-section.md) <br/> | A  *y-*  coordinate of a point on the infinite line.  <br/> |
|[Ellipse](ellipse-row-geometry-section.md) <br/> | The  *y*  -coordinate of the center of the ellipse.  <br/> |
   
## Remarks

To get a reference to the Y cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Geometry  *i*  .Y  *j*            where  *i*  and  *j*  = <1>, 2, 3...  <br/> |
|| Geometry  *i*  .Y1 (InfiniteLine and Ellipse rows)            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Y cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Row index:  <br/> |**visRowVertex** +  *j*            where  *j*  = 0, 1, 2...  <br/> |
||**visRowVertex** (InfiniteLine and Ellipse rows)  <br/> |
| Cell index:  <br/> |**visY** (MoveTo, LineTo, ArcTo, EllipticalArcTo, NURBSTo, Polyline, SplineStart, and SplineKnot rows)  <br/> |
||**visInfiniteLineY1** (InfiniteLine row)  <br/> |
||**visEllipseCenterY** (Ellipse row)  <br/> |
   

