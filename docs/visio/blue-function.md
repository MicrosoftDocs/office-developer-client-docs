---
title: "BLUE Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251402
 
localization_priority: Normal
ms.assetid: da9fb933-4e2c-3e2a-1879-6e70db0cd830
description: "Returns the blue component of a color. The return value is an integer in the range of 0 to 255, inclusive. The function returns 0 for invalid input."
---

# BLUE Function

Returns the blue component of a color. The return value is an integer in the range of 0 to 255, inclusive. The function returns 0 for invalid input.
  
## Syntax

BLUE(** *expression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**String** <br/> |An index of a color in the document's color table, an expression that resolves to a custom color (like RGB or HSL), or a reference to a cell that contains a color index or color result.  <br/> |
   
### Return value

Integer
  
## Example 1

BLUE(Sheet.4!FillForegnd)
  
Returns the blue component of Sheet.4's fill foreground color.
  
## Example 2

BLUE(13)
  
Returns 128 if the document uses the default Visio color palette, where cyan is the color at index 13.
  
## Example 3

BLUE(RGB(10, 20, 30))
  
Returns 30.
  

