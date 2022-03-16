---
title: "EventDblClick Cell (Events Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251312
 
ms.localizationpriority: medium
ms.assetid: ca949013-f998-1bce-39e5-ac6f68ab2392
description: "An event cell that is evaluated when a shape is double-clicked."
---

# EventDblClick Cell (Events Section)

An event cell that is evaluated when a shape is double-clicked.
  
## Remarks

Event cells are evaluated only when the event occurs, not upon formula entry.
  
To get a reference to the EventDblClick cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | EventDblClick  <br/> |
   
To get a reference to the EventDblClick cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowEvent** <br/> |
| **Cell index:**  <br/> |**visEvtCellDblClick** <br/> |
   

