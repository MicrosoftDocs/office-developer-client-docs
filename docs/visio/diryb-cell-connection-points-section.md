---
title: "DirY / B Cell (Connection Points Section)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm240
 
ms.localizationpriority: medium
ms.assetid: d951c57d-2c22-0289-35af-44e3c2877b2c

description: "Determines the y -component for the required alignment vector of a matching connection point. It is also used to orient the attached leg of a dynamic connector. This cell takes a floating point value."
---

# DirY / B Cell (Connection Points Section)

Determines the *y* -component for the required alignment vector of a matching connection point. It is also used to orient the attached leg of a dynamic connector. This cell takes a floating point value.
  
## Remarks

To get a reference to the DirY / B cell by name from another formula, or from a program using the **CellsU** property, use:
  
|||
|:-----|:-----|
|Cell name:  <br/> |Connections.DirY[*i*]           <br/>where *i* = <1>, 2, 3... |

To get a reference to the DirY / B cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionConnectionPts** <br/> |
|Row index:  <br/> |**visRowConnectionPts** + *i*           <br/>where *i* = 0, 1, 2... |
|Cell index:  <br/> |**visCnnctDirY** (non-extended rows)          <br/>**visCnnctB** (extended rows)  <br/> |

For information about non-extended and extended rows, see Connection Points row.
  