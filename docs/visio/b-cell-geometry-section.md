---
title: "B Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251751
 
localization_priority: Normal
ms.assetid: b0fb6a47-47d8-ab9c-854d-0b0bbfdfcc27

description: "Represents different information in different rows. This table describes the B cell based on the row in which it's located."
---

# B Cell (Geometry Section)

Represents different information in different rows. This table describes the B cell based on the row in which it's located.
  
|**Row**|**Description**|
|:-----|:-----|
|[EllipticalArcTo](ellipticalarcto-row-geometry-section.md) <br/> | The  *y*  -coordinate of an arc's control point.  <br/> |
|[NURBSTo](nurbsto-row-geometry-section.md) <br/> | The last weight of the nonuniform rational B-spline (NURBS).  <br/> |
|[SplineStart](splinestart-row-geometry-section.md) <br/> | The first knot of a spline.  <br/> |
|[InfiniteLine](infiniteline-row-geometry-section.md) <br/> | A  *y*  -coordinate of a point on an infinite line; paired with  *x*  -coordinate represented by the [A](a-cell-geometry-section.md) cell.  <br/> |
|[Ellipse](ellipse-row-geometry-section.md) <br/> | A  *y*  -coordinate of a point on an ellipse; paired with  *x*  -coordinate represented by the [A](a-cell-geometry-section.md) cell.  <br/> |
   
## Remarks

To get a reference to the B cell by name from another formula, or from a program, using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Geometry  *i*  .B  *j*            where  *i*  and  *j*  = <1>, 2, 3...  <br/> |
|| Geometry  *i*  .B1 (InfiniteLine and Ellipse rows)  <br/> |
   
To get a reference to the B cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Row index:  <br/> |**visRowVertex** +  *j*            where  *j*  = 0, 1, 2...  <br/> |
||**visRowVertex** (InfiniteLine and Ellipse rows)  <br/> |
| Cell index:  <br/> |**visControlX** (EllipticalArcTo row)  <br/> |
||**visControlY** (EllipticalArcTo row)  <br/> |
||**visNURBSWeight** (NURBSTo row)  <br/> |
||**visSplineKnot2** (SplineStart row)  <br/> |
||**visInfiniteLineY2** (InfiniteLine row)  <br/> |
||**visEllipseMajorY** (Ellipse row)  <br/> |
   

