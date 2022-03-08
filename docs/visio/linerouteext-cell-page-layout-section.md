---
title: "LineRouteExt Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm50115
 
ms.localizationpriority: medium
ms.assetid: 3d16b8b3-601b-c10b-68a8-ffd47251306f
description: "Determines the default appearance for all connectors on a drawing page."
---

# LineRouteExt Cell (Page Layout Section)

Determines the default appearance for all connectors on a drawing page.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Default (straight)  <br/> |**visLORouteExtDefault** <br/> |
| 1  <br/> | Straight  <br/> |**visLORouteExtStraight** <br/> |
| 2  <br/> | Curved  <br/> |**visLORouteExtNURBS** <br/> |
   
## Remarks

To get a reference to the LineRouteExt cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LineRouteExt  <br/> |
   
To get a reference to the LineRouteExt cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPageLayout** <br/> |
| **Cell index:**  <br/> |**visPLOLineRouteExt** <br/> |
   

