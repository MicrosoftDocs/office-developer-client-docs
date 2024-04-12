---
title: "EventXFMod Cell (Events Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251313
 
ms.localizationpriority: medium
ms.assetid: b88588a2-c651-7eab-9c7a-ed78f20d1ba3
description: "An event cell that is evaluated when a shape's position or orientation on the page is transformed (XF)."
---

# EventXFMod Cell (Events Section)

An event cell that is evaluated when a shape's position or orientation on the page is transformed ("XF").
  
## Remarks

Event cells are evaluated only when the event occurs, not upon formula entry.
  
To get a reference to the EventXFMod cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | EventXFMod  <br/> |
   
To get a reference to the EventXFMod cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowEvent** <br/> |
| **Cell index:**  <br/> |**visEvtCellXFMod** <br/> |
   

