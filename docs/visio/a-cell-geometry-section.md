---
title: "A Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm51215
 
localization_priority: Normal
ms.assetid: 6853df0f-d22e-89ca-7d34-342b9c0bea23
description: "Represents different information in different rows. This table describes the A cell based on the row in which it's located."
---

# A Cell (Geometry Section)

Represents different information in different rows. This table describes the A cell based on the row in which it's located.
  
|**Row**|**Description**|
|:-----|:-----|
|[ArcTo](arcto-row-geometry-section.md) <br/> | The distance from the arc's midpoint to the midpoint of its chord.  <br/> |
|[EllipticalArcTo](ellipticalarcto-row-geometry-section.md) <br/> | The  *x*  -coordinate of the arc's control point, a point on the arc. The control point is best located about halfway between the beginning and ending vertices of the arc. Otherwise, the arc may grow to an extreme size in order to pass through the control point, with unpredictable results.  <br/> |
|[PolylineTo](polylineto-row-geometry-section.md) <br/> | The polyline formula.  <br/> |
|[NURBSTo](nurbsto-row-geometry-section.md) <br/> | The second to the last knot of the nonuniform rational B-spline (NURBS).  <br/> |
|[SplineStart](splinestart-row-geometry-section.md) <br/> | The second knot of the spline.  <br/> |
|[SplineKnot](splineknot-row-geometry-section.md) <br/> | One of the spline's knots (other than the last one or the first two).  <br/> |
|[InfiniteLine](infiniteline-row-geometry-section.md) <br/> | An  *x*  -coordinate of a point on the infinite line; paired with  *y*  -coordinate represented by the [B](b-cell-geometry-section.md) cell.  <br/> |
|[Ellipse](ellipse-row-geometry-section.md) <br/> | An  *x*  -coordinate of a point on the ellipse; paired with  *y*  -coordinate represented by the [B](b-cell-geometry-section.md) cell.  <br/> |
   
## Remarks

To get a reference to the A cell by name from another formula, or from a program, using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Geometry  *i*  .A  *j*            where  *i*  and  *j*  = <1>, 2, 3...  <br/> |
|| Geometry  *i*  .A1 (InfiniteLine and Ellipse rows)            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the A cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Row index:  <br/> |**visRowVertex** +  *j*            where  *j*  = 0, 1, 2...  <br/> |
||**visRowVertex** (InfiniteLine and Ellipse rows)  <br/> |
| Cell index:  <br/> |**visBow** (ArcTo row)  <br/> |
||**visControlX** (EllipticalArcTo row)  <br/> |
||**visControlY** (EllipticalArcTo row)  <br/> |
||**visPolylineData** (Polyline row)  <br/> |
||**visNURBSKnot** (NURBSTo row)  <br/> |
||**visSplineKnot** (SplineStart and SplineKnot rows)  <br/> |
||**visInfiniteLineX2** (InfiniteLine row)  <br/> |
||**visEllipseMajorX** (Ellipse row)  <br/> |
   

