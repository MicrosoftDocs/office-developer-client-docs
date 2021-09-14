---
title: "RED Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251487
 
ms.localizationpriority: medium
ms.assetid: a95fd86d-ebc1-66b6-e7d9-9c8ea84d23ab
description: "Returns the red component of a color."
---

# RED Function

Returns the red component of a color. 
  
## Syntax

RED(** *expression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**Varies** <br/> |An index of a color in the document's color table, an expression that resolves to a custom color (like RGB or HSL), or a reference to a cell that contains a color index or color result.  <br/> |
   
### Return value

Number
  
## Remarks

The return value is a number in the range 0 to 255, inclusive, or a cell reference that resolves to an index. If  _expression_ is invalid, this function returns 0 (black). 
  
## Example 1

RED(22)
  
Returns 51 if the document uses the default Microsoft Office Visio color palette, where dark gray is the color at index 22.
  
## Example 2

RED(Char.Color)
  
Returns the value of the red component of the current font color.
  
## Example 3

RED(RGB(10, 20, 30))
  
Returns 10.
  

