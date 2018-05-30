---
title: "LineToNodeY Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251650
 
localization_priority: Normal
ms.assetid: 49d649e8-1603-192b-2984-e5d0b713da89
description: "Determines the vertical clearance between all connectors and shapes on the drawing page."
---

# LineToNodeY Cell (Page Layout Section)

Determines the vertical clearance between all connectors and shapes on the drawing page.
  
## Remarks

You can also set the value of this cell in the **Layout and Routing Spacing** dialog box. (On the **Design** tab, click the **Page Setup** arrow, click **Layout and Routing**, and then click **Spacing**.)
  
To get a reference to the LineToNodeY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LineToNodeY  <br/> |
   
To get a reference to the LineToNodeY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOLineToNodeY** <br/> |
   

