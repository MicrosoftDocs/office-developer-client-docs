---
title: "Tip Cell (Controls Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1010
 
localization_priority: Normal
ms.assetid: 7fd11650-fffa-1316-d302-3122ac5feb14

description: "Represents a descriptive text string that appears as a tool tip when a user pauses the pointer over a shape's control handle. The application automatically encloses the tip string in quotation marks in the cell, but the quotation marks are not displayed in the tool tip."
---

# Tip Cell (Controls Section)

Represents a descriptive text string that appears as a tool tip when a user pauses the pointer over a shape's control handle. The application automatically encloses the tip string in quotation marks in the cell, but the quotation marks are not displayed in the tool tip.
  
## Remarks

To get a reference to the Tip cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Controls.  *name*  .Tipwhere Controls.  *name*  is the name of the controls row.  <br/> |
   
To get a reference to the Tip cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionControls** <br/> |
| Row index:  <br/> |**visRowControl** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCtlTip** <br/> |
   

