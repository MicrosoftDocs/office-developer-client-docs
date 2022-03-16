---
title: "DisplayMode Cell (Group Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251623
 
ms.localizationpriority: medium
ms.assetid: e6d72529-aa03-e94b-130c-79ed04336299
description: "Determines how the group shape and its members are displayed."
---

# DisplayMode Cell (Group Properties Section)

Determines how the group shape and its members are displayed.
  
|**Value**|**Display Mode**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Hides the group shape and text. |**visGrpDispModeNone** <br/> |
|1  <br/> |Displays the group shape behind member shapes. |**visGrpDispModeBack** <br/> |
|2  <br/> |Displays the group shape in front of member shapes. |**visGrpDispModeFront** <br/> |
   
## Remarks

You can also set this value by selecting the group, clicking **Behavior** on the **Shape Design** group on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then selecting a display mode from the **Group data** list. 
  
To get a reference to the DisplayMode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |DisplayMode  <br/> |
   
To get a reference to the DisplayMode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowGroup** <br/> |
|**Cell index:**  <br/> |**visGroupDisplayMode** <br/> |
   

