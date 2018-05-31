---
title: "ConLineRouteExt Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm50110
 
localization_priority: Normal
ms.assetid: cafd7589-1c94-b9bc-b1a6-40f7c15fba71
description: "Determines the appearance of a connector."
---

# ConLineRouteExt Cell (Shape Layout Section)

Determines the appearance of a connector.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Default; use page setting  <br/> |**visLORouteExtDefault** <br/> |
| 1  <br/> | Straight  <br/> |**visLORouteExtStraight** <br/> |
| 2  <br/> | Curved  <br/> |**visLORouteExtNURBS** <br/> |
   
## Remarks

To get a reference to the ConLineRouteExt cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ConLineRouteExt  <br/> |
   
To get a reference to the ConLineRouteExt cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowShapeLayout** <br/> |
| Cell index:  <br/> |**visSLOLineRouteExt** <br/> |
   

