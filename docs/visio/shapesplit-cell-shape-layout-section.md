---
title: "ShapeSplit Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60080
 
ms.localizationpriority: medium
ms.assetid: 96b8c503-67b3-8623-d99b-0dad7b15c224
description: "Indicates whether this shape can split shapes that are splittable."
---

# ShapeSplit Cell (Shape Layout Section)

Indicates whether this shape can split shapes that are splittable.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Do not allow this shape to split other shapes. |**visSLOSplitNone** <br/> |
| 1  <br/> | Allow this shape to split other shapes. |**visSLOSplitAllow** <br/> |
   
## Remarks

A shape that can split other shapes must be either a 2-D shape or a 1-D placeable shape. 
  
Automatic splitting of shapes is enabled and disabled at three different levels: application, page, and shape. By default, splitting is enabled at the application and page level; for shapes, it varies by drawing type. 
  
To enable or disable splitting at the application level, use the **Enable connector splitting** setting on the **Advanced** tab of the **Visio Options** dialog box (click the **File** tab, click **Options**, and then click **Advanced**). 
  
To enable or disable splitting on a page, see the PageShapeSplit cell. 
  
To cause a 1-D shape to be splittable, see the ShapeSplittable cell.
  
To get a reference to the ShapeSplit cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ShapeSplit  <br/> |
   
To get a reference to the ShapeSplit cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowShapeLayout** <br/> |
| **Cell index:**  <br/> |**visSLOSplit** <br/> |
   

