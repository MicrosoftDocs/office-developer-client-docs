---
title: "NoSnap Cell (Geometry Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm740
 
ms.localizationpriority: medium
ms.assetid: 0e6c8621-868c-9eac-926b-3049f18023b0

description: "Determines whether other shapes snap to a path."
---

# NoSnap Cell (Geometry Section)

Determines whether other shapes snap to a path.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Do not allow other shapes to snap to this path. |
| FALSE  <br/> | Allow other shapes to snap to this path. |
   
## Remarks

To get a reference to the NoSnap cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Geometry  *i*  .NoSnap            where  *i*  = <1>, 2, 3... |
   
To get a reference to the NoSnap cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2... |
| **Row index:**  <br/> |**visRowComponent** <br/> |
| **Cell index:**  <br/> |**visCompNoSnap** <br/> |
   

