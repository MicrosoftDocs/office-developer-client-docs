---
title: "Denoise Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm225
 
localization_priority: Normal
ms.assetid: e305585f-f0d8-0494-91d4-0c76929dc170
description: "Removes noise (pixels with randomly distributed color levels) from a bitmap image. The default value is 0%."
---

# Denoise Cell (Image Properties Section)

Removes noise (pixels with randomly distributed color levels) from a bitmap image. The default value is 0%.
  
## Remarks

To get a reference to the Denoise cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Denoise  <br/> |
   
To get a reference to the Denoise cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowImage** <br/> |
| Cell index:  <br/> |**visImageDenoise** <br/> |
   

