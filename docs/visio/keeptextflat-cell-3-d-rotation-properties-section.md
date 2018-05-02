---
title: "KeepTextFlat Cell (3-D Rotation Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 3537de44-8d6f-4bd9-bf8c-fa851fc007b9
description: "Indicates whether a shape's text will ignore the shape's rotation in 3-D. Does not apply to 2-D rotation."
---

# KeepTextFlat Cell (3-D Rotation Properties Section)

Indicates whether a shape's text will ignore the shape's rotation in 3-D. Does not apply to 2-D rotation. 
  
****

|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Shape text does not rotate with the shape's geometry.  <br/> |
|FALSE  <br/> |Shape text is transformed to rotate with the shape's geometry.  <br/> |
   
## Remarks

To get a reference to the **KeepTextFlat** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |KeepTextFlat  <br/> |
   
To get a reference to the **KeepTextFlat** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRow3DRotationProperties** <br/> |
|Cell index:  <br/> |**visKeepTextFlat** <br/> |
   

