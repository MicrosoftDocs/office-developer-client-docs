---
title: "PaperKind Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60067
 
ms.localizationpriority: medium
ms.assetid: b2c9616f-a144-eb99-54b6-b53745c7b4d6
description: "Specifies the type of paper on which to print the page."
---

# PaperKind Cell (Print Properties Section)

Specifies the type of paper on which to print the page.
  
## Remarks

This setting corresponds to the **Paper Size** setting in the **Print Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow, and then on the **Print Setup** tab, click the **Setup** button). 
  
The numeric values in this cell map to constants (prefixed with DMPAPER) defined for paper selections in the Microsoft Windows wingdi.h file. 
  
To get a reference to the PaperKind cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |PaperKind  <br/> |
   
To get a reference to the PaperKind cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPrintProperties** <br/> |
|**Cell index:**  <br/> |**visPrintPropertiesPaperKind** <br/> |
   

