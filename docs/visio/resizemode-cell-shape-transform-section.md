---
title: "ResizeMode Cell (Shape Transform Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251203
 
ms.localizationpriority: medium
ms.assetid: 49816e46-fa83-3ee4-1451-9c85fbd0f519
description: "Shows the current resize behavior setting for the shape."
---

# ResizeMode Cell (Shape Transform Section)

Shows the current resize behavior setting for the shape.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Use group's setting. |**visXFormResizeDontCare** <br/> |
|1  <br/> |Reposition only. |**visXFormResizeSpread** <br/> |
|2  <br/> |Scale with group. |**visXFormResizeScale** <br/> |
   
## Remarks

You can also set this value on the **Behavior** tab in the **Behavior** dialog box (on the [Developer](run-in-developer-mode-display-the-developer-tab.md)tab, in the **Shape Design** group, click **Behavior**). To get a reference to the ResizeMode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ResizeMode  <br/> |
   
To get a reference to the ResizeMode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowXFormOut** <br/> |
|**Cell index:**  <br/> |**visXFormResizeMode** <br/> |
   

