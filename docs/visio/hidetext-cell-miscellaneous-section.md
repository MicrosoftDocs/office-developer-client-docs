---
title: "HideText Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251323
 
localization_priority: Normal
ms.assetid: 3d23647a-e567-da71-50df-336a0f2f4071
description: "Hides the text for a shape. You can view text, edit properties, and apply styles to the text in the text block, although the changes will not appear until you reset HideText to FALSE (0)."
---

# HideText Cell (Miscellaneous Section)

Hides the text for a shape. You can view text, edit properties, and apply styles to the text in the text block, although the changes will not appear until you reset HideText to FALSE (0).
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Text is hidden and does not print.  <br/> |
| FALSE  <br/> | Text is not hidden.  <br/> |
   
## Remarks

To get a reference to the HideText cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | HideText  <br/> |
   
To get a reference to the HideText cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visHideText** <br/> |
   

