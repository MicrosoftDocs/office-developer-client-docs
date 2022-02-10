---
title: "NoLiveDynamics Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm720
 
ms.localizationpriority: medium
ms.assetid: d1c4b9d9-6d64-8ed1-9fc6-2dbf829a75b5
description: "Determines whether a shape dynamically resizes or rotates as you are manipulating it."
---

# NoLiveDynamics Cell (Miscellaneous Section)

Determines whether a shape dynamically resizes or rotates as you are manipulating it.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Do not dynamically update the shape while you are manipulating it. |
| FALSE  <br/> | Dynamically update the shape while you are manipulating it. |
   
## Remarks

As you resize or rotate a two-dimensional (2-D) shape without live dynamics, you see a selection box. If the shape is one-dimensional (1-D), the visual feedback is based on the value of the DynFeedback cell.
  
To get a reference to the NoLiveDynamics cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | NoLiveDynamics  <br/> |
   
To get a reference to the NoLiveDynamics cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visNoLiveDynamics** <br/> |
   

