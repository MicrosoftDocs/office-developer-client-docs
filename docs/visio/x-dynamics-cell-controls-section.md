---
title: "X Dynamics Cell (Controls Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1145
 
ms.localizationpriority: medium
ms.assetid: 9757dfb4-6d37-0517-17fe-7593ff12bbfe

description: "Represents the x -coordinate for a control handle's anchor point in local coordinates."
---

# X Dynamics Cell (Controls Section)

Represents the  *x*  -coordinate for a control handle's anchor point in local coordinates. 
  
## Remarks

The anchor point is used for rubber-banding during dynamics.
  
To get a reference to the X Dynamics cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Controls.  *name*  .XDynwhere Controls.  *name*  is the name of the controls row.  <br/> |
   
To get a reference to the X Dynamics cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionControls** <br/> |
| Row index:  <br/> |**visRowControl** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCtlXDyn** <br/> |
   

