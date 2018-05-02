---
title: "C Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm140
 
localization_priority: Normal
ms.assetid: d51a1dd8-678a-a34d-658d-bd7a027dd379

description: "Represents different information in different rows. This table describes the C cell based on the row in which it's located."
---

# C Cell (Geometry Section)

Represents different information in different rows. This table describes the C cell based on the row in which it's located.
  
|**Row**|**Description**|
|:-----|:-----|
|[EllipticalArcTo](ellipticalarcto-row-geometry-section.md) <br/> | The angle of an arc's major axis relative to the  *x*  -axis of its parent.  <br/> |
|[NURBSTo](nurbsto-row-geometry-section.md) <br/> | The first knot of the nonuniform rational B-spline (NURBS).  <br/> |
|[SplineStart](splinestart-row-geometry-section.md) <br/> | The last knot of a spline.  <br/> |
|[Ellipse](ellipse-row-geometry-section.md) <br/> | An  *x*  -coordinate of a point on an ellipse; paired with the  *y*  -coordinate represented by the [D](d-cell-geometry-section.md) cell.  <br/> |
   
## Remarks

To get a reference to the C cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Geometry  *i*  .C  *j*            where  *i*  and  *j*  = <1>, 2, 3...  <br/> |
|| Geometry  *i*  .C1 (Ellipse row)  <br/> |
   
To get a reference to the C cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Row index:  <br/> |**visRowVertex** +  *j*            where  *j*  = 0, 1, 2...  <br/> |
||**visRowVertex** (Ellipse row)  <br/> |
| Cell index:  <br/> |**visEccentricityAngle** (EllipticalArcTo row)  <br/> |
||**visNURBSKnotPrev** (NURBSTo row)  <br/> |
||**visSplineKnot3** (SplineStart row)  <br/> |
||**visEllipseMinorX** (Ellipse row)  <br/> |
   

