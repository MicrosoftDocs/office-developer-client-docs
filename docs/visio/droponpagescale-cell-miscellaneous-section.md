---
title: "DropOnPageScale Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60042
 
localization_priority: Normal
ms.assetid: 8927f811-7d8e-ed54-9eec-b86a781168dd

---

# DropOnPageScale Cell (Miscellaneous Section)

Contains the percentage by which a shape is scaled when dropped on the drawing page.
  
## Remarks

In the following two cases, Visio scales shapes so that they appear appropriately on the drawing page:
  
- When unmeasured shapes are dropped onto scaled drawings.
    
- When measured shapes are dropped onto unscaled drawings.
    
The percentage in the DropOnPageScale cell indicates the factor by which Visio scaled the shape, either up (\>100) or down (\<100). You can use this number as a factor when calculating hard-coded values. 
  
This value is 100% for measured shapes on scaled drawings or unmeasured shapes on unscaled drawings. 
  
To get a reference to the DropOnPageScale cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | DropOnPageScale  <br/> |
   
To get a reference to the DropOnPageScale cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visObjDropOnPageScale** <br/> |
   

