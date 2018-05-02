---
title: "ImgOffsetY Cell (Foreign Image Info Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm455
 
localization_priority: Normal
ms.assetid: 3b2991aa-4722-fe3b-39c5-02d38c4c7efc
description: "Determines the distance the object is offset vertically from the origin of the object's border. The default is 0. Panning the object with the Crop tool changes this value."
---

# ImgOffsetY Cell (Foreign Image Info Section)

Determines the distance the object is offset vertically from the origin of the object's border. The default is 0. Panning the object with the **Crop** tool changes this value. 
  
## Remarks

To get a reference to the ImgOffsetY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ImgOffsetY  <br/> |
   
To get a reference to the ImgOffsetY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowForeign** <br/> |
| Cell index:  <br/> |**visFrgnImgOffsetY** <br/> |
   

