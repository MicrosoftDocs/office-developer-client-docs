---
title: "ImgOffsetX Cell (Foreign Image Info Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251308
 
localization_priority: Normal
ms.assetid: c079fb10-4db7-4657-75d2-2fb953c86670
description: "Determines the distance the object is offset horizontally from the origin of the object's border. The default is 0. Panning the object with the Crop tool changes this value."
---

# ImgOffsetX Cell (Foreign Image Info Section)

Determines the distance the object is offset horizontally from the origin of the object's border. The default is 0. Panning the object with the **Crop** tool changes this value. 
  
## Remarks

To get a reference to the ImgOffsetX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ImgOffsetX  <br/> |
   
To get a reference to the ImgOffsetX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowForeign** <br/> |
| Cell index:  <br/> |**visFrgnImgOffsetX** <br/> |
   

