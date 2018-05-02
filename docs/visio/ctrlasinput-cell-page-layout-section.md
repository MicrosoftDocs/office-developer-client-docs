---
title: "CtrlAsInput Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1225
 
localization_priority: Normal
ms.assetid: c6fd0aba-7c33-b77f-207b-ba704b3e0756
description: "Determines which shape is the parent when using shapes with control handles. This cell sets the behavior for all the shapes on the drawing page."
---

# CtrlAsInput Cell (Page Layout Section)

Determines which shape is the parent when using shapes with control handles. This cell sets the behavior for all the shapes on the drawing page.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Set the shape that the control handle is connected to as the parent.  <br/> |
| FALSE  <br/> | The default. Set shape that contains the control handle as the parent.  <br/> |
   
## Remarks

To get a reference to the CtrlAsInput cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | CtrlAsInput  <br/> |
   
To get a reference to the CtrlAsInput cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOCtrlAsInput** <br/> |
   

