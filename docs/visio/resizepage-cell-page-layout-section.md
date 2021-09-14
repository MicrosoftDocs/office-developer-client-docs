---
title: "ResizePage Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm850
 
ms.localizationpriority: medium
ms.assetid: d63fe874-1027-3436-dbc1-73e722bce22e
description: "Determines whether to enlarge the page to enclose the drawing after laying out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options)."
---

# ResizePage Cell (Page Layout Section)

Determines whether to enlarge the page to enclose the drawing after laying out shapes by using the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout** Page, and then click **More Layout Options**).
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Enlarge the page.  <br/> |
| FALSE  <br/> | Do not enlarge the page.  <br/> |
   
## Remarks

To get a reference to the ResizePage cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ResizePage  <br/> |
   
To get a reference to the ResizePage cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOResizePage** <br/> |
   

