---
title: "NoLine Cell (Geometry Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm715
 
localization_priority: Normal
ms.assetid: f9624af2-c087-3dde-9140-339c438b3652

description: "Determines whether a line is drawn around the boundary of the path."
---

# NoLine Cell (Geometry Section)

Determines whether a line is drawn around the boundary of the path.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | A line is not drawn around the boundary of the path that is the boundary of a filled region.  <br/> |
| FALSE  <br/> | A line is drawn around the boundary of a path.  <br/> |
   
## Remarks

When you change the color of a line to white, the line still exists even though you can't see it on a white background. When you set the value of this cell to TRUE, no line is drawn.
  
To get a reference to the NoLine cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Geometry  *i*  .NoLine            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the NoLine cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionFirstComponent** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Row index:  <br/> |**visRowComponent** <br/> |
| Cell index:  <br/> |**visCompNoLine** <br/> |
   

