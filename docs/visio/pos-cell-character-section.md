---
title: "Pos Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm805
 
ms.localizationpriority: medium
ms.assetid: c02186ce-6a20-fbe7-588d-d64c3ea4dec4

description: "Determines the position of the shape's text relative to the baseline."
---

# Pos Cell (Character Section)

Determines the position of the shape's text relative to the baseline.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Normal position  <br/> |**visPosNormal** <br/> |
| 1  <br/> | Superscript  <br/> |**visPosSuper** <br/> |
| 2  <br/> | Subscript  <br/> |**visPosSub** <br/> |
   
## Remarks

To get a reference to the Pos cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Char.Pos[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Pos cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionCharacter** <br/> |
| Row index:  <br/> |**visRowCharacter** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visCharacterPos** <br/> |
   

