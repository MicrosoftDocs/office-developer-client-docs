---
title: "CompoundType Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 3e2a88ad-d92c-4550-8da3-fa7fdd032e73
description: "Determines the compound type of the line of a shape."
---

# CompoundType Cell (Line Format Section)

Determines the compound type of the line of a shape. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Simple  <br/> |
|1  <br/> |Double  <br/> |
|2  <br/> |Thick thin  <br/> |
|3  <br/> |Thin thick  <br/> |
|4  <br/> |Triple  <br/> |
   
## Remarks

To get a reference to the **CompoundType** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | CompoundType  <br/> |
   
To get a reference to the **CompoundType** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLine** <br/> |
| **Cell index:**  <br/> |**visCompoundType** <br/> |
   

