---
title: "LineWeight Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm585
 
localization_priority: Normal
ms.assetid: 16b0e293-eeef-34b4-aeb0-4472815dd543
description: "Determines the line weight of a shape. Set the line weight by entering a number with a valid unit of measure."
---

# LineWeight Cell (Line Format Section)

Determines the line weight of a shape. Set the line weight by entering a number with a valid unit of measure.
  
## Remarks

You can also set the value of LineWeight in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Weight**, and then click **More Lines**).
  
If the unit of measure is not entered, the unit of measure for text specified in the **Visio Options** dialog box is used (click the **File** tab, and then click **Options**). Line weight is independent of the scale of the drawing. If the drawing is scaled, the line weight remains the same. 
  
To get a reference to the LineWeight cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LineWeight  <br/> |
   
To get a reference to the LineWeight cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLine** <br/> |
| Cell index:  <br/> |**visLineWeight** <br/> |
   

