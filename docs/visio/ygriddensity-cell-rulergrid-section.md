---
title: "YGridDensity Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251363
 
localization_priority: Normal
ms.assetid: 3ea2b3c7-0c69-a9f2-379f-8daa0c665810
description: "Specifies the type of vertical grid to use."
---

# YGridDensity Cell (Ruler &amp; Grid Section)

Specifies the type of vertical grid to use.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Fixed  <br/> |**visGridFixed** <br/> |
|2  <br/> |Coarse  <br/> |**visGridCoarse** <br/> |
|4  <br/> |Normal (default)  <br/> |**visGridNormal** <br/> |
|8  <br/> |Fine  <br/> |**visGridFine** <br/> |
   
## Remarks

This cell corresponds to the vertical **Grid spacing** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the YGridDensity cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |YGridDensity  <br/> |
   
To get a reference to the YGridDensity cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowRulerGrid** <br/> |
|Cell index:  <br/> |**visYGridDensity** <br/> |
   

