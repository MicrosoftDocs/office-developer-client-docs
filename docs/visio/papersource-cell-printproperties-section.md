---
title: "PaperSource Cell (PrintProperties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60068
 
ms.localizationpriority: medium
ms.assetid: 771a2ab4-578d-51c3-fabd-138f7952bb11
description: "Determines the paper source for the page."
---

# PaperSource Cell (PrintProperties Section)

Determines the paper source for the page. 
  
## Remarks

This setting corresponds to the **Paper Source** setting in the **Print Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow, and then on the **Print Setup** tab, click **Setup**).
  
The numeric values in this cell map to constants (prefixed with DMBIN) defined for bin selections in the Microsoft Windows wingdi.h file; for example, the value 7 represents DMBIN_AUTO. 
  
To get a reference to the PaperSource cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |PaperSource  <br/> |
   
To get a reference to the PaperSource cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPrintProperties** <br/> |
|Cell index:  <br/> |**visPrintPropertiesPaperSource** <br/> |
   

