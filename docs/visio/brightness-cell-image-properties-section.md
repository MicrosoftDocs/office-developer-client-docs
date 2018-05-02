---
title: "Brightness Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251608
 
localization_priority: Normal
ms.assetid: 5bb1cc81-f3fd-a835-1449-233dbd1a62b6
description: "Adjusts the brightness of a bitmap image. Decrease brightness of an image by entering a value between 0% and 49%, or increase brightness by entering a value between 51% and 100%. The default value is 50%."
---

# Brightness Cell (Image Properties Section)

Adjusts the brightness of a bitmap image. Decrease brightness of an image by entering a value between 0% and 49%, or increase brightness by entering a value between 51% and 100%. The default value is 50%.
  
## Remarks

To get a reference to the Brightness cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Brightness  <br/> |
   
To get a reference to the Brightness cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowImage** <br/> |
| Cell index:  <br/> |**visImageBrightness** <br/> |
   

