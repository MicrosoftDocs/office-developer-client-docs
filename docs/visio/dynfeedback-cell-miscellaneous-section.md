---
title: "DynFeedback Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251317
 
ms.localizationpriority: medium
ms.assetid: 44017319-7146-3431-e476-fbb1a40341ca
description: "Changes the type of visual feedback provided to users when they drag a connector. When the mouse button is released, the resulting connector shape is not affected by this setting. This setting does not apply to routable connectors."
---

# DynFeedback Cell (Miscellaneous Section)

Changes the type of visual feedback provided to users when they drag a connector. When the mouse button is released, the resulting connector shape is not affected by this setting. This setting does not apply to routable connectors.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Remains straight (no legs). |**visDynFBDefault** <br/> |
| 1  <br/> | Shows three legs when dragged. |**visDynFBUCon3Leg** <br/> |
| 2  <br/> | Shows five legs when dragged. |**visDynFBUCon5Leg** <br/> |
   
## Remarks

To get a reference to the DynFeedback cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | DynFeedback  <br/> |
   
To get a reference to the DynFeedback cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowMisc** <br/> |
| **Cell index:**  <br/> |**visDynFeedback** <br/> |
   

