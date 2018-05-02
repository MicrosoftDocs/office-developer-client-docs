---
title: "Y Dynamics Cell (Controls Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251284
 
localization_priority: Normal
ms.assetid: cb221974-2f1a-edb0-477b-39a3c4a64c56

description: "Represents the y -coordinate for a control handle's anchor point in local coordinates. The anchor point is used for rubber-banding during dynamics."
---

# Y Dynamics Cell (Controls Section)

Represents the  *y*  -coordinate for a control handle's anchor point in local coordinates. The anchor point is used for rubber-banding during dynamics. 
  
## Remarks

To get a reference to the Y Dynamics cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Controls.  *name*  .YDynwhere Controls.  *name*  is the name of the controls row.  <br/> |
   
To get a reference to the Y Dynamics cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionControls** <br/> |
| Row index:  <br/> |**visRowControl** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCtlYDyn** <br/> |
   

