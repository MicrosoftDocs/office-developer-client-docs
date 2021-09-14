---
title: "XGridOrigin Cell (Ruler &amp; Grid Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1155
 
ms.localizationpriority: medium
ms.assetid: 2b1a8902-b1d4-c3d9-8c9f-1a28fddacc59
description: "Specifies the horizontal coordinate of the grid origin."
---

# XGridOrigin Cell (Ruler &amp; Grid Section)

Specifies the horizontal coordinate of the grid origin.
  
## Remarks

This cell corresponds to the horizontal **Grid origin** option in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow. 
  
To get a reference to the XGridOrigin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |XGridOrigin  <br/> |
   
To get a reference to the XGridOrigin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowRulerGrid** <br/> |
|Cell index:  <br/> |**visXGridOrigin** <br/> |
   

