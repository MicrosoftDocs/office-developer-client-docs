---
title: "ShapeSplittable Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60081
 
ms.localizationpriority: medium
ms.assetid: 6330304a-71f3-62b4-1b27-14495e3f12c3
description: "Indicates whether this 1-D shape can be split."
---

# ShapeSplittable Cell (Shape Layout Section)

Indicates whether this 1-D shape can be split. 
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Do not allow this shape to be split. |**visSLOSplittableNone** <br/> |
| 1  <br/> | Allow this shape to be split. |**visSLOSplittableAllow** <br/> |
   
## Remarks

The default behavior for connectors and other 1-D shapes varies by drawing type. 
  
Automatic splitting of shapes is enabled and disabled at three different levels: application, page, and shape. By default, splitting is enabled at the application level and page levels. 
  
To enable or disable splitting at the application level, use the **Enable connector splitting** setting on the **Advanced** tab of the **Visio Options** dialog box (click the **File** tab, click **Options**, and then click **Advanced** ). 
  
To enable or disable splitting on a page, see the [PageShapeSplit](pageshapesplit-cell-page-layout-section.md) cell. 
  
To cause a shape to be able to split 1-D splittable shapes, see the [ShapeSplit](shapesplit-cell-shape-layout-section.md) cell. 
  
To get a reference to the ShapeSplittable cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ShapeSplittable  <br/> |
   
To get a reference to the ShapeSplittable cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowShapeLayout** <br/> |
| **Cell index:**  <br/> |**visSLOSplittable** <br/> |
   

