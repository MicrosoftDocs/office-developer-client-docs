---
title: "SETF Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251496
 
localization_priority: Normal
ms.assetid: fcf415c1-171f-b75f-6e40-2bbdbe8b1cfb
description: "Sets a cell's formula."
---

# SETF Function

Sets a cell's formula. 
  
## Syntax

SETF( GETREF(** *cell* ** ), ** *formula* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cell_ <br/> |Required  <br/> |**String** <br/> |The cell whose formula to set.  <br/> |
| _formula_ <br/> |Required  <br/> |**String** <br/> |The formula to use.  <br/> |
   
## Remarks

When evaluated, the result of the expression in  _formula_ becomes the new formula in  _cell_. If  _formula_ is enclosed in quotation marks, the quoted expression is written to  _cell_. To set  _cell_ to a string, enclose  _formula_ in three sets of quotation marks. 
  
The target cell must be specified using a GETREF() reference or as a string to avoid circularity. Using GETREF is preferred, because Microsoft Visio can adjust references when the shape is moved to a different document.
  
If  _cell_ is not specified using GETREF or as a string, the function returns an error, and no cell's formula is changed. If  _formula_ contains a syntax error, the function returns an error, and the formula in  _cell_ is not changed. 
  
## Example 1

SETF( GETREF(Scratch.A1), 1.5 in \* 6 + 1 ft)
  
Sets the formula of Scratch.A1 to 21 inches.
  
## Example 2

SETF( GETREF(Scratch.A1), "1.5 in \* 6 + 1 ft")
  
Sets the formula of Scratch. A1 to the expression 1.5 in\*6+1 ft.
  
## Example 3

SETF( GETREF(Scratch.A1), """Say """"ahh""""""")
  
Sets the formula of Scratch.A1 to the string "Say ""ahh""" which evaluates to Say "ahh".
  

