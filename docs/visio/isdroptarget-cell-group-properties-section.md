---
title: "IsDropTarget Cell (Group Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm495
 
localization_priority: Normal
ms.assetid: 8140fc7b-b99c-54bb-7af3-7de6fcdae7d3
description: "Determines whether the group allows you to add a shape to it by dropping it on the group."
---

# IsDropTarget Cell (Group Properties Section)

Determines whether the group allows you to add a shape to it by dropping it on the group.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Can add a shape to the group by dropping it onto the group.  <br/> |
|FALSE  <br/> |Cannot drop shape onto the group.  <br/> |
   
## Remarks

You can also set this value by selecting the group, clicking **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then selecting the **Accept dropped shapes** check box. 
  
To add a shape to a group by dropping it on the group, you must also enable similar shape behavior. You must select the shape, click **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then select the **Add shape to groups on drop** check box. This value is stored in the IsDropSource cell in the Miscellaneous section. 
  
To get a reference to the IsDropTarget cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |IsDropTarget  <br/> |
   
To get a reference to the IsDropTarget cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowGroup** <br/> |
|Cell index:  <br/> |**visGroupIsDropTarget** <br/> |
   

