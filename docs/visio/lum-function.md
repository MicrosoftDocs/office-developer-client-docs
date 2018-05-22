---
title: "LUM Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251460
 
localization_priority: Normal
ms.assetid: 38e6bba7-1bf2-3d31-0912-707002454f5d
description: "Returns the value of a color's luminosity component."
---

# LUM Function

Returns the value of a color's luminosity component.
  
## Syntax

LUM(** *expression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**Numeric** <br/> |The index of a color in the document's color table, or a reference to a cell that contains a color index.  <br/> |
   
### Return value

Number
  
## Remarks

The return value is a number in the range 0 to 240, inclusive. The function returns 0 for invalid input. 
  
## Example 1

LUM(Sheet.4!FillForegnd)
  
Returns the luminosity of Sheet.4's fill foreground color.
  
## Example 2

LUM(6)
  
Returns 120 if the document uses the default Visio color palette, where magenta is the color at index 6.
  
## Example 3

LUM(HSL(10, 20, 30))
  
Returns 30.
  

