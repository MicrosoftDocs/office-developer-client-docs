---
title: "SortKey Cell (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60086
 
ms.localizationpriority: medium
ms.assetid: 93d7b00c-bd34-6b4e-44fe-afeb8aa9a294
description: "A number that determines the order of hyperlinks that appear on a shortcut menu."
---

# SortKey Cell (Hyperlinks Section)

A number that determines the order of hyperlinks that appear on a shortcut menu.
  
## Remarks

The hyperlinks on a shortcut menu appear on the menu sorted from lowest to highest, with lower numbers appearing at the top of the menu. If two hyperlink rows have the same SortKey cell value, the order is determined by physical row order. The default is 0 (zero). 
  
To get a reference to the SortKey cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Hyperlink. *name*  .SortKey where Hyperlink  *.name*  is the row name  <br/> |
   
To get a reference to the SortKey cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionHyperlink** <br/> |
|Row index:  <br/> |**visRow1stHyperlink** +  *i*  where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visHLinkSortKey** <br/> |
   

