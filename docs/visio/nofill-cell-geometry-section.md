---
title: "NoFill Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm710
 
ms.localizationpriority: medium
ms.assetid: 0ba7f6da-681b-b749-fe72-afbca23d7e16

description: "Indicates whether a path can be filled."
---

# NoFill Cell (Geometry Section)

Indicates whether a path can be filled.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | The path is not filled even if other paths in the shape are filled. |
| FALSE  <br/> | The shape's fill applies to the path, even if it isn't closed. |
   
## Remarks

If you set a shape's fill pattern to none (0), none of its paths are filled. This cell is used to turn the fill off selectively for a path within a shape.
  
To get a reference to the NoFill cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Geometry  *i*  .NoFill            where  *i*  = <1>, 2, 3... |
   
To get a reference to the NoFill cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2... |
| **Row index:**  <br/> |**visRowComponent** <br/> |
| **Cell index:**  <br/> |**visCompNoFill** <br/> |
   

