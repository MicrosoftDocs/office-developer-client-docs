---
title: "BevelMaterialType Cell (Bevel Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 30f50a94-88dc-41a3-bb46-45c92d6817a4
description: "Determines the type of material the bevel is composed of."
---

# BevelMaterialType Cell (Bevel Properties Section)

Determines the type of material the bevel is composed of. 
  
|**Description**|**Value**|
|:-----|:-----|
|0  <br/> |No special material  <br/> |
|1  <br/> |Matte  <br/> |
|2  <br/> |Warm Matte  <br/> |
|3  <br/> |Plastic  <br/> |
|4  <br/> |Metal  <br/> |
|5  <br/> |Dark Edge  <br/> |
|6  <br/> |Soft Edge  <br/> |
|7  <br/> |Flat  <br/> |
|8  <br/> |Wireframe  <br/> |
|9  <br/> |Powder  <br/> |
|10  <br/> |Translucent Powder  <br/> |
|11  <br/> |Clear  <br/> |
   
## Remarks

To get a reference to the **BevelMaterialType** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | BevelMaterialType  <br/> |
   
To get a reference to the **BevelMaterialType** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowBevelProperties** <br/> |
| Cell index:  <br/> |**visBevelMaterialType** <br/> |
   

