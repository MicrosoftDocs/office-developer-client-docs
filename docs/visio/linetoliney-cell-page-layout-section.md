---
title: "LineToLineY Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm570
 
localization_priority: Normal
ms.assetid: db9a8232-25c5-7087-2ae9-50470d0cf16e
description: "Determines the vertical clearance between all connectors on the drawing page."
---

# LineToLineY Cell (Page Layout Section)

Determines the vertical clearance between all connectors on the drawing page.
  
## Remarks

You can also set the value of this cell in the **Layout and Routing Spacing** dialog box. (On the **Design** tab, click the **Page Setup** arrow, click **Layout and Routing**, and then click **Spacing**.)
  
To get a reference to the LineToLineY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineToLineY  <br/> |
   
To get a reference to the LineToLineY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPageLayout** <br/> |
|Cell index:  <br/> |**visPLOLineToLineY** <br/> |
   

