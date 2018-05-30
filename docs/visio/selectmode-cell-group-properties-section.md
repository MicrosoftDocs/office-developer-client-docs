---
title: "SelectMode Cell (Group Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm875
 
localization_priority: Normal
ms.assetid: 5ba68e05-f394-d7b7-390d-f0a9fdad011e
description: "Determines how you select a group shape and its members."
---

# SelectMode Cell (Group Properties Section)

Determines how you select a group shape and its members.
  
|**Value**|**Selection mode**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Select the group shape only.  <br/> |**visGrpSelModeGroupOnly** <br/> |
|1  <br/> |Select the group shape first.  <br/> |**visGrpSelModeGroup1st** <br/> |
|2  <br/> |Select the members of the group first.  <br/> |**visGrpSelModeMembers1st** <br/> |
   
## Remarks

You can also set this value in the **Behavior** dialog box (with the group shape selected, on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, in the **Shape Design** group, click **Behavior**, and then click a mode in the **Selection** list under **Group Behavior** ). 
  
To get a reference to the SelectMode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |SelectMode  <br/> |
   
To get a reference to the SelectMode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowGroup** <br/> |
|Cell index:  <br/> |**visGroupSelectMode** <br/> |
   

