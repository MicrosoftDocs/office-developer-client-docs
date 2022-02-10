---
title: "Y Cell (Controls Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251282
 
ms.localizationpriority: medium
ms.assetid: dd7ea5fa-1d34-44e8-5a29-69ca542aecba

description: "Represents the y -coordinate that indicates the location of a shape's control handle in local coordinates."
---

# Y Cell (Controls Section)

Represents the  *y*  -coordinate that indicates the location of a shape's control handle in local coordinates. 
  
## Remarks

To get a reference to the Y cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Controls.  *name*  .Ywhere Controls.  *name*  is the name of the controls row. |
   
To get a reference to the Y cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionControls** <br/> |
| Row index:  <br/> |**visRowControl** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visCtlY** <br/> |
   

