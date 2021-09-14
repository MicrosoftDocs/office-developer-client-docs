---
title: "ReplaceLockShapeData Cell (Change Shape Behavior Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6a089266-7b19-4310-8cb5-4373ea3b2d64
description: "Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. The ReplaceLockShapeData determines whether the shape data of the master shape overwrites all of the shape data of the shape being replaced."
---

# ReplaceLockShapeData Cell (Change Shape Behavior Section)

Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. The **ReplaceLockShapeData** determines whether the shape data of the master shape overwrites all of the shape data of the shape being replaced. 
  
|**Value**|**Description**|
|:-----|:-----|
|1 (TRUE)  <br/> |All rows and values of the **Shape Data** section of the master shape are copied onto the replacement shape and any local values from the old shape being replaced are discarded.  <br/> |
|0 (FALSE)  <br/> |The rows and values of the **Shape Data** section of the master shape are copied to the replacement shape. Any rows in the **Shape Data** section of the old shape with local values are transferred to the replacement shape.  <br/> |
   
## Remarks

To get a reference to the **ReplaceLockShapeData** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ReplaceLockShapeData  <br/> |
   
To get a reference to the **ReplaceLockShapeData** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowReplaceBehaviors** <br/> |
| Cell index:  <br/> |**visReplaceLockShapeData** <br/> |
   

