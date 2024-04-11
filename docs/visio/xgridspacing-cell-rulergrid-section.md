---
title: "XGridSpacing Cell (Ruler &amp; Grid Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1160
 
ms.localizationpriority: medium
ms.assetid: e07dd983-7588-6317-944c-46da2bb65b31
description: "Specifies the distance between horizontal lines in a fixed grid (XGridDensity = 0)."
---

# XGridSpacing Cell (Ruler &amp; Grid Section)

Specifies the distance between horizontal lines in a fixed grid (XGridDensity = 0).
  
## Remarks

This cell corresponds to the horizontal **Minimum spacing** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the XGridSpacing cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |XGridSpacing  <br/> |
   
To get a reference to the XGridSpacing cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowRulerGrid** <br/> |
|**Cell index:**  <br/> |**visXGridSpacing** <br/> |
   

