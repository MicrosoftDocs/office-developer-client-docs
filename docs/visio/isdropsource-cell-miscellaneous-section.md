---
title: "IsDropSource Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm490
 
ms.localizationpriority: medium
ms.assetid: 3b20e6ef-f1ac-5bb0-5ac3-4df3ae5e9bf9
description: "Determines whether the shape can be added to a group by dropping it onto the group."
---

# IsDropSource Cell (Miscellaneous Section)

Determines whether the shape can be added to a group by dropping it onto the group.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Can add the shape to a group by dropping it onto the group. |
|FALSE  <br/> |Cannot add the shape to a group. |
   
## Remarks

You can also set this value by selecting the shape, clicking **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then selecting the **Add shape to groups on drop** check box. 
  
In addition to enabling this behavior for a shape, you must also enable a group to accept shapes that are dragged into it. To do so, select the group, click **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then select the **Accept dropped shapes** check box. This value is stored in the IsDropTarget cell in the Group Properties section. 
  
To get a reference to the IsDropSource cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |IsDropSource  <br/> |
   
To get a reference to the IsDropSource cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowMisc** <br/> |
|Cell index:  <br/> |**visDropSource** <br/> |
   

