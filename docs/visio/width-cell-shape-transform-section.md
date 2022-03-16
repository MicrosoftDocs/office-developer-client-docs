---
title: "Width Cell (Shape Transform Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251194
 
ms.localizationpriority: medium
ms.assetid: 992ae9d8-ea15-0f5c-ccd6-e4c536099692
description: "Contains the width of the selected shape in drawing units. The default formula for determining the width of a 1-D shape is:"
---

# Width Cell (Shape Transform Section)

Contains the width of the selected shape in drawing units. The default formula for determining the width of a 1-D shape is:
  
= SQRT((EndX - BeginX) ^ 2 + (EndY - BeginY) ^ 2)
  
## Remarks

To get a reference to the Width cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Width  <br/> |
   
To get a reference to the Width cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowXFormOut** <br/> |
| **Cell index:**  <br/> |**visXFormWidth** <br/> |
   

