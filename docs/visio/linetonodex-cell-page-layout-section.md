---
title: "LineToNodeX Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm575
 
ms.localizationpriority: medium
ms.assetid: 9d58e23e-b411-c5c1-b785-5014488d42c8
description: "Determines the horizontal clearance between all connectors and shapes on the drawing page."
---

# LineToNodeX Cell (Page Layout Section)

Determines the horizontal clearance between all connectors and shapes on the drawing page.
  
## Remarks

You can also set the value of this cell in the **Layout and Routing Spacing** dialog box. (On the **Design** tab, click the **Page Setup** arrow, click **Layout and Routing**, and then click **Spacing**.)
  
To get a reference to the LineToNodeY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |LineToNodeX  <br/> |
   
To get a reference to the LineToNodeX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPageLayout** <br/> |
|**Cell index:**  <br/> |**visPLOLineToNodeX** <br/> |
   

