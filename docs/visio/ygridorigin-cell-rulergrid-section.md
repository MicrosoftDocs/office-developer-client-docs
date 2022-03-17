---
title: "YGridOrigin Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1205
 
ms.localizationpriority: medium
ms.assetid: eeec59f8-f301-5639-ffd6-8a36b2bf9c8f
description: "Specifies the vertical origin of the grid."
---

# YGridOrigin Cell (Ruler &amp; Grid Section)

Specifies the vertical origin of the grid.
  
## Remarks

This cell corresponds to the vertical **Grid origin** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the YGridOrigin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |YGridOrigin  <br/> |
   
To get a reference to the YGridOrigin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowRulerGrid** <br/> |
|**Cell index:**  <br/> |**visYGridOrigin** <br/> |
   

