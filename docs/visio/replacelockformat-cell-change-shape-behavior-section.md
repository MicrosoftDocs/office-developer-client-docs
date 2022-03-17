---
title: "ReplaceLockFormat Cell (Change Shape Behavior Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6973e2e6-7e7f-48ba-95b3-37c959f6ffb1
description: "Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. If the ReplaceLockFormat cell of a master shape is set to TRUE (1), the formatting values of the master overwrite all corresponding values of a shape being replaced by the master."
---

# ReplaceLockFormat Cell (Change Shape Behavior Section)

Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. If the **ReplaceLockFormat** cell of a master shape is set to TRUE (1), the formatting values of the master overwrite all corresponding values of a shape being replaced by the master. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |If the **ReplaceLockFormat** cell of a master shape is set to TRUE, the formatting values of the master overwrite all corresponding values of a shape being replaced by the master. |
|FALSE  <br/> |If the **ReplaceLockFormat** cell of a master shape is set to FALSE, the replacement shape contains the local formatting values from the old shape after the replacement operation. |
   
## Remarks

The **ReplaceLockFormat** cell determines whether the master shape overwrites the local formatting values of the cells in the following sections during a shape replacement operation: 
  
- **Fill Format** section 
    
- **Line Format** section 
    
- **Quick Style** section 
    
- **Theme Properties** section 
    
- **Gradient Properties** section 
    
- **Bevel Properties** section 
    
- **Additional Effect Properties** section 
    
- **Line Gradient Stops** section 
    
- **Fill Gradient Stops** section 
    
To get a reference to the **ReplaceLockFormat** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ReplaceLockFormat  <br/> |
   
To get a reference to the **ReplaceLockFormat** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowReplaceBehaviors** <br/> |
| **Cell index:**  <br/> |**visReplaceLockFormat** <br/> |
   

