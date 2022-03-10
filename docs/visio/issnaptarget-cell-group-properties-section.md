---
title: "IsSnapTarget Cell (Group Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251626
 
ms.localizationpriority: medium
ms.assetid: b58131f6-a566-d9ca-bad4-4f4b66e03aaf
description: "Determines whether you snap to a group or to shapes within the group."
---

# IsSnapTarget Cell (Group Properties Section)

Determines whether you snap to a group or to shapes within the group.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Enable snapping to shapes within a group. |
|FALSE  <br/> |Snap only to the group. |
   
## Remarks

You can also set this value by selecting the group, clicking **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then selecting the **Snap to member shapes** check box. 
  
To get a reference to the IsSnapTarget cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |IsSnapTarget  <br/> |
   
To get a reference to the IsSnapTarget cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowGroup** <br/> |
|**Cell index:**  <br/> |**visGroupIsSnapTarget** <br/> |
   

