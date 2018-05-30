---
title: "BeginArrowSize Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251629
 
localization_priority: Normal
ms.assetid: bfddb829-6e13-7d74-b9b9-2cb5c0937bae
description: "Determines the size of the arrowhead at the beginning of the line."
---

# BeginArrowSize Cell (Line Format Section)

Determines the size of the arrowhead at the beginning of the line.
  
|**Value**|**Size**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Very small  <br/> |**visArrowSizeVerySmall** <br/> |
| 1  <br/> | Small  <br/> |**visArrowSizeSmall** <br/> |
| 2  <br/> | Medium  <br/> |**visArrowSizeMedium** <br/> |
| 3  <br/> | Large  <br/> |**visArrowSizeLarge** <br/> |
| 4  <br/> | Very large  <br/> |**visArrowSizeVeryLarge** <br/> |
| 5  <br/> | Jumbo  <br/> |**visArrowSizeJumbo** <br/> |
| 6  <br/> | Colossal  <br/> |**visArrowSizeColossal** <br/> |
   
## Remarks

You can also set the size of the arrowhead in the **Line** dialog box. 
  
To get a reference to the BeginArrowSize cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | BeginArrowSize  <br/> |
   
To get a reference to the BeginArrowSize cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLine** <br/> |
| Cell index:  <br/> |**visLineBeginArrowSize** <br/> |
   

