---
title: "ConLineJumpStyle Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251655
 
ms.localizationpriority: medium
ms.assetid: baa05a50-97d0-3769-635e-0ea20317d59a
description: "Determines the line jump style for line jumps on a dynamic connector."
---

# ConLineJumpStyle Cell (Shape Layout Section)

Determines the line jump style for line jumps on a dynamic connector.
  
|**Value**|**Line Jump Style**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Page default  <br/> |**visLOJumpStyleDefault** <br/> |
|1  <br/> |Arc  <br/> |**visLOJumpStyleArc** <br/> |
|2  <br/> |Gap  <br/> |**visLOJumpStyleGap** <br/> |
|3  <br/> |Square  <br/> |**visLOJumpStyleSquare** <br/> |
|4  <br/> |Triangle  <br/> |**visLOJumpStyleTriangle** <br/> |
|5  <br/> |3 sides  <br/> |**visLOJumpStyle2Point** <br/> |
|6  <br/> |4 sides  <br/> |**visLOJumpStyle3Point** <br/> |
|7  <br/> |5 sides  <br/> |**visLOJumpStyle4Point** <br/> |
|8  <br/> |6 sides  <br/> |**visLOJumpStyle5Point** <br/> |
|9  <br/> |7 sides  <br/> |**visLOJumpStyle6Point** <br/> |
   
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLOJumpStyle** <br/> |
   
## Remarks

You can also set the value of this cell by selecting a dynamic connector, clicking **Behavior** in the **Shape Design** group on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then clicking the **Connector** tab. 
  
To get a reference to the ConLineJumpStyle cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ConLineJumpStyle  <br/> |
   
To get a reference to the ConLineJumpStyle cell by index from a program, use the **CellsSRC** property with the following arguments: 
  

