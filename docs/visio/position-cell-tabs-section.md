---
title: "Position Cell (Tabs Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251755
 
localization_priority: Normal
ms.assetid: 40d7e38e-b3b0-8616-ed27-1f963a841e03

description: "Specifies the position of a tab stop. The tab position is independent of the scale of the drawing. If the drawing is scaled, the tab position remains the same."
---

# Position Cell (Tabs Section)

Specifies the position of a tab stop. The tab position is independent of the scale of the drawing. If the drawing is scaled, the tab position remains the same.
  
## Remarks

To get a reference to the Position cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Tabs.  *ij*            where  *i*  and  *j*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Position cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTab** <br/> |
| Row index:  <br/> |**visRowTab** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> | (*j*  *3) + **visTabPos** <br/> |
   

