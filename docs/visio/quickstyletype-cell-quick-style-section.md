---
title: "QuickStyleType Cell (Quick Style Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: e7470417-0d70-433e-9496-604ca2eafee6
description: "Determines the type of Quick Style (2-dimensional, 1-dimensional, or connector) that the shape inherits."
---

# QuickStyleType Cell (Quick Style Section)

Determines the type of Quick Style (2-dimensional, 1-dimensional, or connector) that the shape inherits. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Visio chooses automatically  <br/> |
|1  <br/> |1-dimensional  <br/> |
|2  <br/> |2-dimensional  <br/> |
|3  <br/> |Connector  <br/> |
   
## Remarks

To get a reference to the **QuickStyleType** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | QuickStyleType  <br/> |
   
To get a reference to the **QuickStyleType** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowQuickStyleProperties** <br/> |
| **Cell index:**  <br/> |**visQuickStyleType** <br/> |
   

