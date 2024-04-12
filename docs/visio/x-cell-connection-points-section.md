---
title: "X Cell (Connection Points Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251746
 
ms.localizationpriority: medium
ms.assetid: 11c69600-4e1f-4c52-ff35-b6a7cc6c734c

description: "Represents the x -coordinate for a connection point in local coordinates."
---

# X Cell (Connection Points Section)

Represents the  *x*  -coordinate for a connection point in local coordinates. 
  
## Remarks

To get a reference to the X cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Connections.X  *i*            where  *i*  = <1>, 2, 3... |
   
To get a reference to the X cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionConnectionPts** <br/> |
| **Row index:**  <br/> |**visRowConnectionPts** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visX** <br/> |
   

