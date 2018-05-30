---
title: "Y Behavior Cell (Controls Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1190
 
localization_priority: Normal
ms.assetid: 6d5062d3-743b-8664-8ec9-5a8f11d5edf9

description: "Controls the type of behavior the y -coordinate of the control handle will exhibit after the handle is moved. These formulas are available."
---

# Y Behavior Cell (Controls Section)

Controls the type of behavior the  *y*  -coordinate of the control handle will exhibit after the handle is moved. These formulas are available. 
  
|**Value**|**Behavior**|**Definition**|**Automation constant**|
|:-----|:-----|:-----|:-----|
| 0  <br/> | Proportional  <br/> | The control handle can be moved, and it also moves in proportion with the shape when it is stretched.  <br/> |**visCtlProportional** <br/> |
| 1  <br/> | Proportional locked  <br/> | The control handle moves in proportion with the shape, but the control handle itself cannot be moved.  <br/> |**visCtlLocked** <br/> |
| 2  <br/> | Offset from bottom edge  <br/> | The control handle is offset a constant distance from the bottom of the shape.  <br/> |**visCtlOffsetMin** <br/> |
| 3  <br/> | Offset from center  <br/> | The control handle is offset a constant distance from the center of the shape.  <br/> |**visCtlOffsetMid** <br/> |
| 4  <br/> | Offset from top edge  <br/> | The control handle is offset a constant distance from the top of the shape.  <br/> |**visCtlOffsetMax** <br/> |
| 5  <br/> | Proportional, hidden  <br/> | Same as 0, but the control handle is not visible.  <br/> |**visCtlProportionalHidden** <br/> |
| 6  <br/> | Proportional locked, hidden  <br/> | Same as 1, but the control handle is not visible.  <br/> |**visCtlLockedHiddenv** <br/> |
| 7  <br/> | Offset from left edge, hidden  <br/> | Same as 2, but the control handle is not visible.  <br/> |**visCtlOffsetMinHidden** <br/> |
| 8  <br/> | Offset from center, hidden  <br/> | Same as 3, but the control handle is not visible.  <br/> |**visCtlOffsetMidHidden** <br/> |
| 9  <br/> | Offset from right edge, hidden  <br/> | Same as 4, but the control handle is not visible.  <br/> |**visCtlOffsetMaxHidden** <br/> |
   
## Remarks

To get a reference to the Y Behavior cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Controls.  *name*  .YConwhere Controls.  *name*  is the name of the controls row.  <br/> |
   
To get a reference to the Y Behavior cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionControls** <br/> |
| Row index:  <br/> |**visRowControl** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCtlYCon** <br/> |
   

