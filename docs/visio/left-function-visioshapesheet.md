---
title: "LEFT Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1021757
 
localization_priority: Normal
ms.assetid: 0c2f6e06-b772-2006-ec7b-8695d097f146
description: "Returns the left-most character or characters in a text string, based on the number of characters you specify."
---

# LEFT Function (VisioShapeSheet)

Returns the left-most character or characters in a text string, based on the number of characters you specify.
  
## Syntax

LEFT(** *text* **, [, ** *num_chars_opt* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _text_ <br/> |Required  <br/> |**String** <br/> |The text string that contains the characters you want to extract.  <br/> |
| _num_chars_opt_ <br/> |Optional  <br/> |**Numeric** <br/> |The number of characters you want to extract.  <br/> |
   
### Return value

String
  
## Remarks

The value of  _num_chars_opt_ must be greater than or equal to zero (0). 
  
If  _num_chars_opt_ is greater than the length of the text, LEFT returns all of the text. If  _num_chars_opt_ is omitted, it is assumed to be 1. 
  
## Example

LEFT ("January 1, 2004", 3) 
  
Returns the value "Jan". 
  

