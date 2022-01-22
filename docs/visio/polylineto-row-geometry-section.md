---
title: "PolylineTo Row (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251757
 
ms.localizationpriority: medium
ms.assetid: b78a993f-4165-438d-39cf-9461b2877f17
description: "Contains x - and y -coordinates of the last point of a polyline and a polyline formula."
---

# PolylineTo Row (Geometry Section)

Contains  *x*  - and  *y*  -coordinates of the last point of a polyline and a polyline formula. 
  
A PolylineTo row contains the following cells.
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-geometry-section.md) <br/> |The *x*  -coordinate of the ending vertex of a polyline.  <br/> |
|[Y](y-cell-geometry-section.md) <br/> |The *y*  -coordinate of the ending vertex of a polyline.  <br/> |
|[A](a-cell-geometry-section.md) <br/> |The polyline formula.  <br/> |
   
## Remarks

Lines represented as a Polyline row are equivalent to lines represented as a sequence of LineTo rows, but a Polyline row is more efficient. You can change a PolylineTo row to a LineTo row so you can easily see the shape geometry. To do this, right-click the PolylineTo row, and then click **Expand Row** on the shortcut menu. 
  
To change a row type to a PolylineTo row, right-click the row, and then click **Change Row Type** on the shortcut menu. 
  

