---
title: "YGridSpacing Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1210
 
ms.localizationpriority: medium
ms.assetid: 30766e13-c90d-62fc-9c98-35ad7b0b4056
description: "Specifies the distance between vertical lines in a fixed grid (YGridDensity = 0)."
---

# YGridSpacing Cell (Ruler &amp; Grid Section)

Specifies the distance between vertical lines in a fixed grid (YGridDensity = 0).
  
## Remarks

Corresponds to the vertical **Minimum spacing** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the YGridSpacing cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |YGridSpacing  <br/> |
   
To get a reference to the YGridSpacing cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowRulerGrid** <br/> |
|**Cell index:**  <br/> |**visYGridSpacing** <br/> |
   

