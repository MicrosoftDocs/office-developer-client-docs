---
title: "XGridDensity Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1150
 
localization_priority: Normal
ms.assetid: db7b353f-4379-8865-1c35-36b89cf93257
description: "Specifies the type of horizontal grid to use."
---

# XGridDensity Cell (Ruler &amp; Grid Section)

Specifies the type of horizontal grid to use.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Fixed  <br/> |**visGridFixed** <br/> |
|2  <br/> |Coarse  <br/> |**visGridCoarse** <br/> |
|4  <br/> |Normal (default)  <br/> |**visGridNormal** <br/> |
|8  <br/> |Fine  <br/> |**visGridFine** <br/> |
   
## Remarks

This cell corresponds to the horizontal **Grid spacing** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow). 
  
To get a reference to the XGridDensity cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |XGridDensity  <br/> |
   
To get a reference to the XGridDensity cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowRulerGrid** <br/> |
|Cell index:  <br/> |**visXGridDensity** <br/> |
   

