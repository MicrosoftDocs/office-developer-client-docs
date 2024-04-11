---
title: "EndArrowSize Cell (Line Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251630
 
ms.localizationpriority: medium
ms.assetid: e2ecf7c0-a0e9-951f-676a-8e5857bb6544
description: "Determines the size of the arrowhead at the end of the line."
---

# EndArrowSize Cell (Line Format Section)

Determines the size of the arrowhead at the end of the line.
  
|**Value**|**Size**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Very small  <br/> |**visArrowSizeVerySmall** <br/> |
|1  <br/> |Small  <br/> |**visArrowSizeSmall** <br/> |
|2  <br/> |Medium  <br/> |**visArrowSizeMedium** <br/> |
|3  <br/> |Large  <br/> |**visArrowSizeLarge** <br/> |
|4  <br/> |Extra large  <br/> |**visArrowSizeVeryLarge** <br/> |
|5  <br/> |Jumbo  <br/> |**visArrowSizeJumbo** <br/> |
|6  <br/> |Colossal  <br/> |**visArrowSizeColossal** <br/> |
   
## Remarks

You can also set this value in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Arrows**, and then click **More Arrows**).
  
To get a reference to the EndArrowSize cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |EndArrowSize  <br/> |
   
To get a reference to the EndArrowSize cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowLine** <br/> |
|**Cell index:**  <br/> |**visLineEndArrowSize** <br/> |
   

