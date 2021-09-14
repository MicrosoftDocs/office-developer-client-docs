---
title: "Can Glue Cell (Controls Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251287
 
ms.localizationpriority: medium
ms.assetid: 1c4c4ae2-b3fa-ed45-c6e5-22bedb2523db

description: "Determines whether a control handle can be glued to other shapes."
---

# Can Glue Cell (Controls Section)

Determines whether a control handle can be glued to other shapes.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Control handle can be glued.  <br/> |
| FALSE  <br/> | Control handle cannot be glued.  <br/> |
   
## Remarks

To get a reference to the Can Glue cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Controls.  *name*  .CanGluewhere Controls.  *name*  is the name of the controls row.  <br/> |
   
To get a reference to the Can Glue cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionControls** <br/> |
| Row index:  <br/> |**visRowControl** +  *i*            where  *i*  = 0, 1, 2, ...  <br/> |
| Cell index:  <br/> |**visCtlGlue** <br/> |
   

