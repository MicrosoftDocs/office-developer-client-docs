---
title: "LineJumpStyle Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251646
 
ms.localizationpriority: medium
ms.assetid: 89f16674-ee1f-f5f9-9830-7bcc52e3a068
description: "Determines the line jump style for all connectors on the drawing page that don't have a local line jump style."
---

# LineJumpStyle Cell (Page Layout Section)

Determines the line jump style for all connectors on the drawing page that don't have a local line jump style.
  
|**Value**|**Line jump style**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Arc  <br/> |**visLOJumpStyleDefault** <br/> |
|1  <br/> |Arc  <br/> |**visLOJumpStyleArc** <br/> |
|2  <br/> |Gap  <br/> |**visLOJumpStyleGap** <br/> |
|3  <br/> |Square  <br/> |**visLOJumpStyleSquare** <br/> |
|4  <br/> |2 sides  <br/> |**visLOJumpStyleTriangle** <br/> |
|5  <br/> |3 sides  <br/> |**visLOJumpStyle2Point** <br/> |
|6  <br/> |4 sides  <br/> |**visLOJumpStyle3Point** <br/> |
|7  <br/> |5 sides  <br/> |**visLOJumpStyle4Point** <br/> |
|8  <br/> |6 sides  <br/> |**visLOJumpStyle5Point** <br/> |
|9  <br/> |7 sides  <br/> |**visLOJumpStyle6Point** <br/> |
   
## Remarks

You can also set the value of this cell on the **Layout and Routing** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow, and then click **Layout and Routing**).
  
To get a reference to the LineJumpStyle cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |LineJumpStyle  <br/> |
   
To get a reference to the LineJumpStyle cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPageLayout** <br/> |
|**Cell index:**  <br/> |**visPLOJumpStyle** <br/> |
   

