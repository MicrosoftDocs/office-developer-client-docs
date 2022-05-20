---
title: "XRulerDensity Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1165
 
ms.localizationpriority: medium
ms.assetid: c11717c5-eb0e-e4fa-5a91-c62ecc048635
description: "Specifies the horizontal subdivisions on the ruler for the page."
---

# XRulerDensity Cell (Ruler &amp; Grid Section)

Specifies the horizontal subdivisions on the ruler for the page.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Fixed  <br/> |**visRulerFixed** <br/> |
|8 (&amp;H8)  <br/> |Coarse  <br/> |**visRulerCoarse** <br/> |
|16 (&amp;H10)  <br/> |Normal (Default)  <br/> |**visRulerNormal** <br/> |
|32 (&amp;H20)  <br/> |Fine  <br/> |**visRulerFine** <br/> |
   
## Remarks

This cell corresponds to the horizontal **Subdivisions** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the XRulerDensity cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |XRulerDensity  <br/> |
   
To get a reference to the XRulerDensity cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowRulerGrid** <br/> |
|**Cell index:**  <br/> |**visXRulerDensity** <br/> |
   

