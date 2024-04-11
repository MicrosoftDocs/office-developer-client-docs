---
title: "Y Cell (Action Tags Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1026934
 
ms.localizationpriority: medium
ms.assetid: b213fc46-7f80-99fd-60ba-8ddf3d0f6ee3

description: "The y -coordinate position in the shape's local coordinates around which the action tag button is placed."
---

# Y Cell (Action Tags Section)

The *y* -coordinate position in the shape's local coordinates around which the action tag button is placed.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags.
  
## Remarks

The X and Y cells define a point in the shape's local coordinates, and the X Justify and Y Justify cells define where to place the action tag button in relation to that point.
  
To get a reference to the Y cell by name from another formula, or from a program using the **CellsU** property, use:
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | SmartTags. *name* .Y where SmartTags. *name* is the name of the action tag row. <br/> |

To get a reference to the Y cell by index from a program, use the **CellsSRC** property with the following arguments:
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionSmartTag** <br/> |
| **Row index:**  <br/> |**visRowSmartTag** + *i* where *i* = 0, 1, 2... |
| **Cell index:**  <br/> |**visSmartTagY** <br/> |
