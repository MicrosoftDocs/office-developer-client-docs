---
title: "Blur Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm115
 
ms.localizationpriority: medium
ms.assetid: 8b077cdb-6036-4f77-dc20-a476bb75b0f7
description: "Blurs or softens a bitmap image. The default value is 0%."
---

# Blur Cell (Image Properties Section)

Blurs or softens a bitmap image. The default value is 0%.
  
## Remarks

To get a reference to the Blur cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Blur  <br/> |
   
To get a reference to the Blur cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowImage** <br/> |
| **Cell index:**  <br/> |**visImageBlur** <br/> |
   

