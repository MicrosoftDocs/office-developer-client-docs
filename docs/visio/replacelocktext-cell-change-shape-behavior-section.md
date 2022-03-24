---
title: "ReplaceLockText Cell (Change Shape Behavior Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 31f43ebe-3758-4fd9-83b5-775041c5890f
description: "Indicates whether the values of specified cells in a master shape overwrite the values of a shape being replaced during a shape replacement operation."
---

# ReplaceLockText Cell (Change Shape Behavior Section)

Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. The **ReplaceLockText** determines whether the text displayed on the Master overwrites the text of the shape being replaced. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> | The text on the master shape overwrites the text on the old shape. In addition, the master shape overwrites the values of the cells in the following sections during a shape replacement operation:  <br/> **Text Fields** section  <br/> **Text Block Format** section  <br/> |
|FALSE  <br/> |The replacement shape contains any text, text fields, or other text properties from the old shape that have been added to the shape. When the replacement shape contains text properties from the old shape, the replacement shape also has the values from the **Character** and **Paragraph** sections of the old shape if they have more than one row. |
   
If set to TRUE (1), the values of the shape Master replaces the values of the following on the shape being replaced:
  
- [TheText Cell (Events Section)](thetext-cell-events-section.md)
    
- Cells in the [Character Section](character-section.md)
    
- Cells in the [Paragraph Section](paragraph-section.md)
    
- Cells in the [Tabs Section](tabs-section.md)
    
## Remarks

To get a reference to the **ReplaceLockText** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ReplaceLockText  <br/> |
   
To get a reference to the **ReplaceLockText** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowReplaceBehaviors** <br/> |
| **Cell index:**  <br/> |**visReplaceLockText** <br/> |
   

