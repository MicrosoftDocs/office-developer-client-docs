---
title: "ImgWidth Cell (Foreign Image Info Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm460
 
localization_priority: Normal
ms.assetid: b57fb962-0b3e-f2e5-3b88-3edf33e40496
description: "Determines the width of the object's image within its border. The default formula is:"
---

# ImgWidth Cell (Foreign Image Info Section)

Determines the width of the object's image within its border. The default formula is:
  
= Width \* 1
  
Cropping the object changes the factor by which Width is multiplied.
  
## Remarks

To get a reference to the ImgWidth cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ImgWidth  <br/> |
   
To get a reference to the ImgWidth cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowForeign** <br/> |
| Cell index:  <br/> |**visFrgnImgWidth** <br/> |
   

