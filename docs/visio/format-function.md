---
title: "FORMAT Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251424
 
localization_priority: Normal
ms.assetid: 52f5ef4d-07c6-ab36-bf74-b30b50eea221
description: "Returns the result of expression as a string formatted according to formatpicture."
---

# FORMAT Function

Returns the result of  _expression_ as a string formatted according to  _formatpicture_.
  
## Syntax

FORMAT( ** *expression* **," ** *formatpicture* ** ") 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**String** <br/> |A combination of constants, operators, functions, and references to ShapeSheet cells that results in a value.  <br/> |
| _formatpicture_ <br/> |Required  <br/> |**String** <br/> |The format picture used to fomat the string.  <br/> |
   
### Return value

String
  
## Remarks

The type of the expression and the type specified in the format picture govern the behavior of the returned string. The  _formatpicture_ must be appropriate for the type of expression. For more information about specifying format pictures, see [About format pictures](about-format-pictures.md).
  
Returns an error if the result of  _expression_ and the type expected in  _formatpicture_ are of a different kind or if there are syntax errors in  _formatpicture_.
  
## Example 1

FORMAT(1cm/4, "0.000 u")
  
Returns "0.250 cm."
  
## Example 2

FORMAT(1cm/4, "0.00 U")
  
Returns "0.25 CM."
  
## Example 3

FORMAT(1cm/4, "0.0 u")
  
Returns "0.3 cm."
  

