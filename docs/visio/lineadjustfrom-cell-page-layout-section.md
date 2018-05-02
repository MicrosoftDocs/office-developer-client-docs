---
title: "LineAdjustFrom Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251887
 
localization_priority: Normal
ms.assetid: 6949c717-dc69-1d17-5215-eb6efce56fcb
description: "Determines which dynamic connectors the application spaces apart if they route on top of each other."
---

# LineAdjustFrom Cell (Page Layout Section)

Determines which dynamic connectors the application spaces apart if they route on top of each other.
  
|**Value**|**Adjustment**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Unrelated lines  <br/> |**visPLOLineAdjustFromNotRelated** <br/> |
|1  <br/> |All lines  <br/> |**visPLOLineAdjustFromAll** <br/> |
|2  <br/> |No lines  <br/> |**visPLOLineAdjustFromNone** <br/> |
|3  <br/> |Routing style default  <br/> |**visPLOLineAdjustFromRoutingDefault** <br/> |
   
## Remarks

You can also set the value of this cell on the **Layout and Routing** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow, and then click **Layout and Routing**).
  
To get a reference to the LineAdjustFrom cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineAdjustFrom  <br/> |
   
To get a reference to the LineAdjustFrom cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPageLayout** <br/> |
|Cell index:  <br/> |**visPLOLineAdjustFrom** <br/> |
   

