---
title: "EventDrop Cell (Events Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm350
 
ms.localizationpriority: medium
ms.assetid: f84afe83-8391-0c13-f442-ea8794b38642
description: "An event cell that is evaluated when a shape is dropped on the drawing page, either as an instance or when the shape is duplicated or pasted."
---

# EventDrop Cell (Events Section)

An event cell that is evaluated when a shape is dropped on the drawing page, either as an instance or when the shape is duplicated or pasted.
  
## Remarks

Event cells are evaluated only when the event occurs, not upon formula entry.
  
To get a reference to the EventDrop cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | EventDrop  <br/> |
   
To get a reference to the EventDrop cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowEvent** <br/> |
| **Cell index:**  <br/> |**visEvtCellDrop** <br/> |
   

