---
title: "Gamma Cell (Image Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm410
 
ms.localizationpriority: medium
ms.assetid: 3dcaee26-391c-0494-4380-890ee825dc47
description: "Adjusts or corrects the intensity of an image for a particular output device, such as a monitor or scanner. The default value is 1 (no correction)."
---

# Gamma Cell (Image Properties Section)

Adjusts or corrects the intensity of an image for a particular output device, such as a monitor or scanner. The default value is 1 (no correction).
  
## Remarks

To get a reference to the Gamma cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Gamma  <br/> |
   
To get a reference to the Gamma cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowImage** <br/> |
| Cell index:  <br/> |**visImageGamma** <br/> |
   

