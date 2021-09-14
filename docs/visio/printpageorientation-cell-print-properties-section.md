---
title: "PrintPageOrientation Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033795
 
ms.localizationpriority: medium
ms.assetid: f8354d0d-0ce2-fb33-ddf7-611a2c24a8be
description: "Determines whether the page prints using portrait or landscape orientation."
---

# PrintPageOrientation Cell (Print Properties Section)

Determines whether the page prints using portrait or landscape orientation.
  
|**Value**|**Orientation**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Same as printer  <br/> |**visPPOSameAsPrinter** <br/> |
| 1  <br/> | Portrait  <br/> |**visPPOPortrait** <br/> |
|2  <br/> |Landscape  <br/> |**visPPOLandscape** <br/> |
   
## Remarks

When you insert new pages in a document, this setting defaults to the setting in the active page.
  
To get a reference to the PrintPageOrientation cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PrintPageOrientation  <br/> |
   
To get a reference to the PrintPageOrientation cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPrintProperties** <br/> |
| Cell index:  <br/> |**visPrintPropertiesPageOrientation** <br/> |
   

