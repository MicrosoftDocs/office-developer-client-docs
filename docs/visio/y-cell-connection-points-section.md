---
title: "Y Cell (Connection Points Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_SDR.chm1175
 
ms.localizationpriority: medium
ms.assetid: 3af6c949-d6a0-9560-54d7-b01a2ad99960

description: "Represents the y -coordinate for a connection point in local coordinates."
---

# Y Cell (Connection Points Section)

Represents the  *y*  -coordinate for a connection point in local coordinates. 
  
## Remarks

To get a reference to the Y cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Connections.Y  *i*            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Y cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionConnectionPts** <br/> |
| **Row index:**  <br/> |**visRowConnectionPts** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visY** <br/> |
   

