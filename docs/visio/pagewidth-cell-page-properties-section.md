---
title: "PageWidth Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251372
 
ms.localizationpriority: medium
ms.assetid: b98c5bf3-10c8-7299-2836-3906d6a9135d
description: "Determines the width of the printed page in drawing units."
---

# PageWidth Cell (Page Properties Section)

Determines the width of the printed page in drawing units.
  
## Remarks

You can also set the page width on the **Page Size** tab of the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow) or by manually resizing the page with the mouse. To do this, drag the edge of the page while holding down the CTRL key. 
  
To get a reference to the PageWidth cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |PageWidth  <br/> |
   
To get a reference to the PageWidth cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPage** <br/> |
|Cell index:  <br/> |**visPageWidth** <br/> |
   

