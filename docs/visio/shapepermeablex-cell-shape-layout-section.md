---
title: "ShapePermeableX Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm890
 
ms.localizationpriority: medium
ms.assetid: 7e27b36c-4fd1-34e0-c168-f49eb5757b0e
description: "Determines whether a connector can route horizontally through a placeable shape."
---

# ShapePermeableX Cell (Shape Layout Section)

Determines whether a connector can route horizontally through a placeable shape.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Enable connectors to route horizontally through a placeable shape. |
|FALSE  <br/> |Do not let connectors route horizontally through a placeable shape. |
   
## Remarks

You can also set the value of this cell on the **Placement** tab in the **Behavior** dialog box (with a shape selected, on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, in the **Shape Design** group, click **Behavior**, and then click the **Placement** tab). 
  
In versions earlier than Visio 2000, you set this behavior by using the ObjInteract cell in the Miscellaneous section. 
  
To get a reference to the ShapePermeableX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ShapePermeableX  <br/> |
   
To get a reference to the ShapePermeableX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowShapeLayout** <br/> |
|**Cell index:**  <br/> |**visSLOPermX** <br/> |
   

