---
title: "OnPage Cell (Print Properties Section)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033793
 
ms.localizationpriority: medium
ms.assetid: 4015506a-e24a-0276-c854-7791a7019067
description: "Indicates whether the drawing is printed on a specific number of printer pages."
---

# OnPage Cell (Print Properties Section)

Indicates whether the drawing is printed on a specific number of printer pages.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Fit the drawing page to a defined number of printer pages. |
|FALSE  <br/> |Do not fit the drawing page to a defined number of printer pages (the default). |

## Remarks

If the OnPage cell is set to TRUE, Microsoft Visio uses the PagesX and PagesY cells to determine the number of printer pages on which to fit the drawing. Values in the ScaleX and ScaleY cells are ignored. This can be considered an "autoscale" setting.
  
This value corresponds to the **Fit to** option on the **Print Setup** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow).
  
To get a reference to the OnPage cell by name from another formula, or from a program using the **CellsU** property, use:
  
|||
|:-----|:-----|
|Cell name:  <br/> |OnPage  <br/> |

To get a reference to the OnPage cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPrintProperties** <br/> |
|Cell index:  <br/> |**visPrintPropertiesOnPage** <br/> |
