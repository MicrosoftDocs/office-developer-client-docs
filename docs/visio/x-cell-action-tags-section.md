---
title: "X Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60093
 
ms.localizationpriority: medium
ms.assetid: d13e362b-9b69-30c5-003a-9c5df2aa29f6

description: "The x -coordinate position in the shape's local coordinates around which the action tag button is placed."
---

# X Cell (Action Tags Section)

The *x*  -coordinate position in the shape's local coordinates around which the action tag button is placed. 
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

The X and Y cells define a point in the shape's local coordinates, and the X Justify and Y Justify cells define where to place the action tag button in relation to that point. 
  
To get a reference to the X cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> |SmartTags. *name*  .X           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the X cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visSmartTagX** <br/> |
   

