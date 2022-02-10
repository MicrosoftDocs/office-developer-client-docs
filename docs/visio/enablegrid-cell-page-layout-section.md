---
title: "EnableGrid Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251642
 
ms.localizationpriority: medium
ms.assetid: bfea4ef4-1b30-eb22-215d-3b9b73098da9
description: "Determines whether the application lays out shapes based on an internal, invisible page grid when you configure the layout in the Configure Layout dialog box. (On the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options.)"
---

# EnableGrid Cell (Page Layout Section)

Determines whether the application lays out shapes based on an internal, invisible page grid when you configure the layout in the **Configure Layout** dialog box. (On the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options**.)
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Use the internal page grid. |
|FALSE  <br/> |Do not use the internal page grid. |
   
## Remarks

You create this page grid by using the **Space between shapes** and the **Average shape size** values in the **Layout and Routing Spacing** dialog box. (On the **Design** tab, click the **Page Setup** arrow, click **Layout and Routing**, and then click **Spacing**.) 
  
When you enable this feature, the application aligns each placeable shape's center point with the center of a block on the internal page grid. 
  
To get a reference to the EnableGrid cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |EnableGrid  <br/> |
   
To get a reference to the EnableGrid cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPageLayout** <br/> |
|Cell index:  <br/> |**visPLOEnableGrid** <br/> |
   

