---
title: "HUE Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251440
 
ms.localizationpriority: medium
ms.assetid: 0f5c6097-eef5-5f58-e2ef-2c348e42dc9a
description: "Returns the value of a color's hue component."
---

# HUE Function

Returns the value of a color's hue component.
  
## Syntax

HUE(** *expression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**String** <br/> |An expression that evaluates to a color. |
   
### Return value

Number
  
## Remarks

The return value is a number in the range 0 to 239, inclusive. The input is an index of a color in the document's color table, an expression that resolves to a custom color (like RGB or HSL), or a reference to a cell that contains a color index or color result. The function returns 0 for invalid input. 
  
## Example 1

HUE(Sheet.4!FillForegnd)
  
Returns the hue of Sheet.4's fill foreground color.
  
## Example 2

HUE(7)
  
Returns 120 if the document uses the default Microsoft Visio color palette, where cyan is the color at index 7.
  
## Example 3

HUE(HSL(10, 20, 30) )
  
Returns 10.
  

