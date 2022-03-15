---
title: "Sharpen Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm910
 
ms.localizationpriority: medium
ms.assetid: aa2bebfc-a6bb-a6b3-3ae9-8553f96b5738
description: "Sharpens a bitmap image. The default value is 0%. Sharpening an image focuses it by increasing the contrast of adjacent pixels."
---

# Sharpen Cell (Image Properties Section)

Sharpens a bitmap image. The default value is 0%. Sharpening an image focuses it by increasing the contrast of adjacent pixels.
  
## Remarks

To get a reference to the Sharpen cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Sharpen  <br/> |
   
To get a reference to the Sharpen cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowImage** <br/> |
| **Cell index:**  <br/> |**visImageSharpen** <br/> |
   

