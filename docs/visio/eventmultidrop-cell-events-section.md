---
title: "EventMultiDrop Cell (Events Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: f496d698-7f08-69cc-4379-df18a2c2fd7e

---

# EventMultiDrop Cell (Events Section)

An event cell that is evaluated when multiple shapes are dropped on the drawing page, either as instances or when shapes are duplicated or pasted.
  
Event cells are evaluated only when the event occurs, not upon formula entry.
  
To refer to the EventMultiDrop cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |EventMultiDrop  <br/> |
   
To refer to the EventMultiDrop cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowEvent** <br/> |
|**Cell index:**  <br/> |**visEvtCellMultiDrop** <br/> |
   

