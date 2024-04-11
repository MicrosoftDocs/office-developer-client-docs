---
title: "IsTextEditTarget Cell (Group Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251627
 
ms.localizationpriority: medium
ms.assetid: 355cef8b-9213-479a-af95-b591f4bc51ad
description: "Determines text assignment for a group."
---

# IsTextEditTarget Cell (Group Properties Section)

Determines text assignment for a group.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Text is added to the group shape. |
|FALSE  <br/> |Text is added to the shape in the group at the top of the stacking order. |
   
## Remarks

You can also set this value by selecting the group, clicking **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then selecting the **Edit text of group** check box. 
  
Groups created in versions earlier than Visio 2000 have a default value of FALSE. Beginning with Visio version 2000, the default value is TRUE. 
  
To get a reference to the IsTextEditTarget cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |IsTextEditTarget  <br/> |
   
To get a reference to the IsTextEditTarget cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowGroup** <br/> |
|**Cell index:**  <br/> |**visGroupIsTextEditTarget** <br/> |
   

