---
title: "LineCap Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251231
 
ms.localizationpriority: medium
ms.assetid: 3519216b-b6cf-2e8c-e20f-adfa373c9028
description: "Indicates whether a line has rounded, square, or extended line caps."
---

# LineCap Cell (Line Format Section)

Indicates whether a line has rounded, square, or extended line caps.
  
|**Value**|**Line end style**|
|:-----|:-----|
|0  <br/> |Rounded  <br/> |
|1  <br/> |Square  <br/> |
|2  <br/> |Extended  <br/> |
   
## Remarks

You can also set the value of this cell in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Arrows**, and then click **More Arrows**).
  
To get a reference to the LineCap cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineCap  <br/> |
   
To get a reference to the LineCap cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowLine** <br/> |
|Cell index:  <br/> |**visLineEndCap** <br/> |
   

