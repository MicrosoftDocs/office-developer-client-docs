---
title: "GlueType Cell (Glue Info Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm420
 
ms.localizationpriority: medium
ms.assetid: fffbefd6-8b0b-0023-6b03-026d1c6e885e
description: "Determines whether a 1-D shape uses static (point-to-point) or dynamic (shape-to-shape) glue when it is glued to another shape."
---

# GlueType Cell (Glue Info Section)

Determines whether a 1-D shape uses static (point-to-point) or dynamic (shape-to-shape) glue when it is glued to another shape.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| &amp;H0  <br/> | Default. Allow dynamic glue for the dynamic connector only; otherwise, use static glue. |**visGlueTypeDefault** <br/> |
| &amp;H1  <br/> | Allow dynamic glue. | Obsolete in Visio 2002  <br/> |
| &amp;H2  <br/> | Allow dynamic glue. |**visGlueTypeWalking** <br/> |
| &amp;H4  <br/> | Do not allow dynamic glue. |**visGlueTypeNoWalking** <br/> |
| &amp;H8  <br/> | Do not allow this 2-D shape to be connected to with dynamic glue. |**visGlueTypeNoWalkingTo** <br/> |
   
## Remarks

If this cell contains a value of 1, 2 or 3, dynamic glue will be established when either of the following occurs:
  
- Shapes are dynamically glued in the user interface.
    
- Shapes are glued to the PinX or PinY cell of another shape from a program.
    
If shapes are glued to shape cells other than PinX or PinY from a program, then static glue is used.
  
Changing this value from allowing to not allowing dynamic glue does not sever or change existing dynamic glue. Programs can establish dynamic glue even if dynamic glue is disabled in the GlueType cell.
  
To get a reference to the GlueType cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | GlueType  <br/> |
   
To get a reference to the GlueType cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowMisc** <br/> |
| **Cell index:**  <br/> |**visGlueType** <br/> |
   

