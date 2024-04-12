---
title: "BeginArrow Cell (Line Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm51105
 
ms.localizationpriority: medium
ms.assetid: 0ab4044e-2d77-1fbe-ef20-5d029bc064ba
description: "Indicates whether a line has an arrowhead or other line end format at its first vertex. Enter a number from 0 to 45 or the USE function with the name of a custom line end, or use the Line dialog box."
---

# BeginArrow Cell (Line Format Section)

Indicates whether a line has an arrowhead or other line end format at its first vertex. Enter a number from 0 to 45 or the USE function with the name of a custom line end, or use the **Line** dialog box. 
  
|**Value**|**Description**|
|:-----|:-----|
| 0  <br/> | No arrowhead. |
| 1 - 45  <br/> | Assorted arrowhead styles that correspond to indexed entries in the **Line** dialog box. |
   
## Remarks

The size of the arrowhead is set in the BeginArrowSize cell.
  
To get a reference to the BeginArrow cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | BeginArrow  <br/> |
   
To get a reference to the BeginArrow cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLine** <br/> |
| **Cell index:**  <br/> |**visLineBeginArrow** <br/> |
   

