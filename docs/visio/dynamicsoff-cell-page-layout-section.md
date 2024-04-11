---
title: "DynamicsOff Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251641
 
ms.localizationpriority: medium
ms.assetid: 055764aa-9681-ffb0-83ce-fdd612fe37af
description: "Determines whether placeable shapes move and connectors reroute around other shapes and connectors on the drawing page."
---

# DynamicsOff Cell (Page Layout Section)

Determines whether placeable shapes move and connectors reroute around other shapes and connectors on the drawing page.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Disable dynamics. |
| FALSE  <br/> | Enable dynamics. |
   
## Remarks

You can disable dynamics to increase your solution's performance. For example, if your solution adds placeable shapes to a drawing and you don't want the application to reroute connectors and reposition shapes each time you add a shape, you can disable dynamics. After your solution adds the shapes, re-enable dynamics.
  
To get a reference to the DynamicsOff cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | DynamicsOff  <br/> |
   
To get a reference to the DynamicsOff cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPageLayout** <br/> |
| **Cell index:**  <br/> |**visPLODynamicsOff** <br/> |
   

