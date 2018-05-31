---
title: "Change Shape Behavior Section"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a9e97f45-2a5c-40c3-8282-a345ae6249d9
description: "Determines the properties that are transferred from the old shape to the replacement shape during a replacement operation. The values of the cells in the Change Shape Behavior section of the Master shape of the replacement are read during the shape replacement operation."
---

# Change Shape Behavior Section

Determines the properties that are transferred from the old shape to the replacement shape during a replacement operation. The values of the cells in the **Change Shape Behavior** section of the Master shape of the replacement are read during the shape replacement operation. 
  
## Remarks

By setting the cells in the **Change Shape Behavior** section, you can ensure that certain properties of the replacement shape remain unchanged during the replacement operation. Properties that are not protected are updated with the local shape values from the old shape during the operation. 
  
You can change the replacement behavior settings of a Master shape by editing the Master shape (in the **Shapes** window, right-click the shape, point to **Edit Master**, and then click **Edit Master Shape**) and changing the values of the [ReplaceCopyCells](replacecopycells-cell-change-shape-behavior-section.md), [ReplaceLockFormat](replacelockformat-cell-change-shape-behavior-section.md), [ReplaceLockShapeData](replacelockshapedata-cell-change-shape-behavior-section.md), and [ReplaceLockText](replacelocktext-cell-change-shape-behavior-section.md) cells in the Master's ShapeSheet. 
  
> [!NOTE]
> You cannot change the shape replacement behaviors of the shapes that are included with the built-in stencils in Microsoft Visio 2013. To modify the shape replacement behaviors of the built-in Visio shapes, create a new stencil and add the shape that you want to modify to the new stencil. 
  

