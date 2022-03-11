---
title: "DirX / A Cell (Connection Points Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251721
 
ms.localizationpriority: medium
ms.assetid: 00d87b92-0da7-37d6-e7b5-23f350db0a9b

description: "Determines the x -component for the required alignment vector of a matching connection point. The DirX / A cell is also used to orient the attached leg of a dynamic connector. This cell takes a floating point value."
---

# DirX / A Cell (Connection Points Section)

Determines the  *x*  -component for the required alignment vector of a matching connection point. The DirX / A cell is also used to orient the attached leg of a dynamic connector. This cell takes a floating point value.
  
## Remarks

To get a reference to the DirX / A cell by name from another formula, or from a program using the **CellsU** property, use:
  
|**Value**|**Description**|
|:-----|:-----|
| Cell name:  <br/> | Connections.DirX[  *i*  ] where  *i*  = <1>, 2, 3... |

To get a reference to the DirX / A cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|**Value**|**Description**|
|:-----|:-----|
| Section index:  <br/> |**visSectionConnectionPts** <br/> |
| Row index:  <br/> |**visRowConnectionPts** + *i*  <br/> where  *i*  = 0, 1, 2  <br/> |
| Cell index:  <br/> |**visCnnctDirX** (non-extended rows)  <br/> **visCnnctA** (extended rows)  <br/> |

For information about non-extended and extended rows, see Connection Points row.
  