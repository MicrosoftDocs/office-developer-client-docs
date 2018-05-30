---
title: "PageHeight Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm760
 
localization_priority: Normal
ms.assetid: 0184814c-2d67-6ad4-e336-5694612e518d
description: "Contains the height of the printed page in drawing units."
---

# PageHeight Cell (Page Properties Section)

Contains the height of the printed page in drawing units.
  
## Remarks

You can also set the page height on the **Page Size** tab of the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow), or by manually resizing the page with the mouse. 
  
To get a reference to the PageHeight cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |PageHeight  <br/> |
   
To get a reference to the PageHeight cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPage** <br/> |
|Cell index:  <br/> |**visPageHeight** <br/> |
   

