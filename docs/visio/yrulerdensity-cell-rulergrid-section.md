---
title: "YRulerDensity Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1215
 
ms.localizationpriority: medium
ms.assetid: aebcd321-9d1c-e04e-7c85-3ec1ed851561
description: "Specifies the vertical subdivisions on the ruler for the page."
---

# YRulerDensity Cell (Ruler &amp; Grid Section)

Specifies the vertical subdivisions on the ruler for the page.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Fixed  <br/> |**visRulerFixed** <br/> |
|8 (&amp;H8)  <br/> |Coarse  <br/> |**visRulerCoarse** <br/> |
|16 (&amp;H10)  <br/> |Normal (Default)  <br/> |**visRulerNormal** <br/> |
|32 (&amp;H20)  <br/> |Fine  <br/> |**visRulerFine** <br/> |
   
## Remarks

This cell corresponds to the vertical **Subdivisions** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the YRulerDensity cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |YRulerDensity  <br/> |
   
To get a reference to the YRulerDensity cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowRulerGrid** <br/> |
|Cell index:  <br/> |**visYRulerDensity** <br/> |
   

