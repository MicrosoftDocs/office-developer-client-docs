---
title: "D Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251753
 
localization_priority: Normal
ms.assetid: 5f1fdf59-db58-561c-e187-1af72a8b87f2

description: "Represents different information in different rows. This table describes the D cell based on the row in which it's located."
---

# D Cell (Geometry Section)

Represents different information in different rows. This table describes the D cell based on the row in which it's located.
  
|**Row**|**Description**|
|:-----|:-----|
|[EllipticalArcTo](ellipticalarcto-row-geometry-section.md) <br/> | The ratio of an arc's major axis to its minor axis. Despite the usual meaning of these words, the "major" axis does not have to be greater than the "minor" axis, so this ratio does not have to be greater than 1. Setting this cell to a value less than or equal to 0 or greater than 1000 can lead to unpredictable results.  <br/> |
|[NURBSTo](nurbsto-row-geometry-section.md) <br/> | The first weight of the nonuniform rational B-spline (NURBS).  <br/> |
|[SplineStart](splinestart-row-geometry-section.md) <br/> | The degree of a spline (an integer from 1 to 25).  <br/> |
|[Ellipse](ellipse-row-geometry-section.md) <br/> | A  *y*  -coordinate of a point on an ellipse; paired with the  *x*  -coordinate represented by the [C](c-cell-geometry-section.md) cell.  <br/> |
   
## Remarks

To get a reference to the D cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Geometry  *i*  .D  *j*            where  *i*  and  *j*  = <1>, 2, 3...  <br/> |
|| Geometry  *i*  .D1 (Ellipse row)            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the D cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Row index:  <br/> |**visRowVertex** +  *j*            where  *j*  = 0, 1, 2...  <br/> |
||**visRowVertex** (Ellipse row)  <br/> |
| Cell index  <br/> |**visAspectRatio** (EllipticalArcTo row)  <br/> |
||**visNURBSWeightPrev** (NURBSTo row)  <br/> |
||**visSplineDegree** (SplineStart row)  <br/> |
||**visEllipseMinorY** (Ellipse row)  <br/> |
   

