---
title: "ShapePermeablePlace Cell (Shape Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm885
 
ms.localizationpriority: medium
ms.assetid: b647cbb5-2769-068d-bbda-2dc983c47ac9
description: "Determines whether placeable shapes can be placed on top of a shape when laying out shapes in the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options)."
---

# ShapePermeablePlace Cell (Shape Layout Section)

Determines whether placeable shapes can be placed on top of a shape when laying out shapes in the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options**).
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Enable shapes to be placed on top of a shape. |
|FALSE  <br/> |Do not enable shapes to be placed on top of a shape. |
   
## Remarks

You can also set the value of this cell on the **Placement** tab in the **Behavior** dialog box (with a shape selected, on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, in the **Shape Design** group, click **Behavior**, and then click the **Placement** tab). 
  
In versions earlier than Visio 2000, you set this behavior using the ObjInteract cell in the Miscellaneous section.
  
To get a reference to the ShapePermeablePlace cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ShapePermeablePlace  <br/> |
   
To get a reference to the ShapePermeablePlace cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowShapeLayout** <br/> |
|**Cell index:**  <br/> |**visSLOPermeablePlace** <br/> |
   

