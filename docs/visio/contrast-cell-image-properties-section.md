---
title: "Contrast Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm200
 
localization_priority: Normal
ms.assetid: f0e4c644-c646-9649-c697-82feb02f5e29
description: "Adjusts the contrast of a bitmap image. Decrease the contrast of an image by entering a value between 0% and 49%, or increase the contrast by entering a value between 51% and 100%. The default value is 50%."
---

# Contrast Cell (Image Properties Section)

Adjusts the contrast of a bitmap image. Decrease the contrast of an image by entering a value between 0% and 49%, or increase the contrast by entering a value between 51% and 100%. The default value is 50%.
  
## Remarks

To get a reference to the Contrast cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Contrast  <br/> |
   
To get a reference to the Contrast cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowImage** <br/> |
| Cell index:  <br/> |**visImageContrast** <br/> |
   

