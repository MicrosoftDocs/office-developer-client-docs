---
title: "LineToLineX Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm565
 
localization_priority: Normal
ms.assetid: f6b461fe-56ac-4c0e-31cd-6b3c1075db6e
description: "Determines the horizontal clearance between all connectors on the drawing page."
---

# LineToLineX Cell (Page Layout Section)

Determines the horizontal clearance between all connectors on the drawing page.
  
## Remarks

You can also set the value of this cell in the **Layout and Routing Spacing** dialog box. (On the **Design** tab, click the **Page Setup** arrow, click **Layout and Routing**, and then click **Spacing**.)
  
To get a reference to the LineToLineX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineToLineX  <br/> |
   
To get a reference to the LineToLineX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPageLayout** <br/> |
|Cell index:  <br/> |**visPLOLineToLineX** <br/> |
   

