---
title: "LocalizeMerge Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033773
 
localization_priority: Normal
ms.assetid: 734d4415-05dd-4c4d-763e-e035fa56dcec
description: "Determines whether shapes are localized when copied between documents."
---

# LocalizeMerge Cell (Miscellaneous Section)

Determines whether shapes are localized when copied between documents.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Localize a shape in the language of the destination document.  <br/> |
| FALSE  <br/> | Do not localize a shape based on the language of the destination document (the default).  <br/> |
   
## Remarks

To get a reference to the LocalizeMerge cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LocalizeMerge  <br/> |
   
To get a reference to the LocalizeMerge cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visObjLocalizeMerge** <br/> |
   

