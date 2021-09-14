---
title: "WalkPreference Cell (Glue Info Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1115
 
ms.localizationpriority: medium
ms.assetid: 08165195-7e4e-f3ab-fa76-fbcacb0a9c9c
description: "Determines whether an endpoint of a 1-D shape moves to a horizontal or vertical connection point on the shape it is glued to, using dynamic glue, when the shape is moved to an ambiguous position. By default, both endpoints of the 1-D shape move to horizontal connection points."
---

# WalkPreference Cell (Glue Info Section)

Determines whether an endpoint of a 1-D shape moves to a horizontal or vertical connection point on the shape it is glued to, using dynamic glue, when the shape is moved to an ambiguous position. By default, both endpoints of the 1-D shape move to horizontal connection points.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 1  <br/> | The begin point of the 1-D shape moves to a vertical connection point, and the endpoint moves to a horizontal connection point (top-to-side or bottom-to-side connections).  <br/> |**visWalkPrefBegNS** <br/> |
| 2  <br/> | The begin point of the 1-D shape moves to a horizontal connection point, and the endpoint moves to a vertical connection point (side-to-top or side-to-bottom connections).  <br/> |**visWalkPrefEndNS** <br/> |
   
## Remarks

This cell has no effect on dynamic connectors. A dynamic connector's behavior is determined by its routing style. See the RouteStyle cell for the default routing style for dynamic connectors on a page, or the ShapeRouteStyle for the routing style of a particular dynamic connector.
  
To get a reference to the WalkPreference cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | WalkPreference  <br/> |
   
To get a reference to the WalkPreference cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visWalkPref** <br/> |
   

