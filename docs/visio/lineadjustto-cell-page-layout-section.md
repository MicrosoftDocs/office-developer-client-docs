---
title: "LineAdjustTo Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm525
 
ms.localizationpriority: medium
ms.assetid: 81cd9670-8a6f-824b-528c-e9b88c86f525
description: "Determines which dynamic connectors line up on top of one another."
---

# LineAdjustTo Cell (Page Layout Section)

Determines which dynamic connectors line up on top of one another.
  
|**Value**|**Adjustment**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Routing style default  <br/> |**visPLOLineAdjustToDefault** <br/> |
|1  <br/> |Lines that are close to each other  <br/> |**visPLOLineAdjustToAll** <br/> |
|2  <br/> |No lines  <br/> |**visPLOLineAdjustToNone** <br/> |
|3  <br/> |Related lines  <br/> |**visPLOLineAdjustToRelated** <br/> |
   
## Remarks

You can also set the value of this cell on the **Layout and Routing** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow, and then click **Layout and Routing**).
  
To get a reference to the LineAdjustTo cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |LineAdjustTo  <br/> |
   
To get a reference to the LineAdjustTo cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPageLayout** <br/> |
|**Cell index:**  <br/> |**visPLOLineAdjustTo** <br/> |
   

