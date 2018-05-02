---
title: "XRulerOrigin Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1170
 
localization_priority: Normal
ms.assetid: 328f8ab5-217f-0336-0d56-611eff509fe8
description: "Specifies the zero point on the x-axis ruler for the page."
---

# XRulerOrigin Cell (Ruler &amp; Grid Section)

Specifies the zero point on the x-axis ruler for the page.
  
## Remarks

This cell corresponds to the horizontal **Ruler zero** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the XRulerOrigin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |XRulerOrigin  <br/> |
   
To get a reference to the XRulerOrigin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowRulerGrid** <br/> |
|Cell index:  <br/> |**visXRulerOrigin** <br/> |
   

