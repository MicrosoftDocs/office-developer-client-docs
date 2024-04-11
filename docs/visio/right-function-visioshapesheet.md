---
title: "RIGHT Function (VisioShapeSheet)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1027314
 
ms.localizationpriority: medium
ms.assetid: 910f0297-d588-2048-f308-03f3c2389bba
description: "Returns the last character or characters in a text string, based on the number of characters you specify."
---

# RIGHT Function (VisioShapeSheet)

Returns the last character or characters in a text string, based on the number of characters you specify.
  
## Syntax

RIGHT(***text*** [, ***num_chars_opt*** ])
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *text* <br/> |Required  <br/> |**String** <br/> | The text string containing the characters you want to extract. |
| *num_chars_opt* <br/> |Optional  <br/> |**Number** <br/> |The number of characters you want to extract. The default is 1. |

### Return value

String
  
## Remarks

The value of *num_chars_opt* must be greater than or equal to zero (0).
  
If *num_chars_opt* is greater than the length of the text, RIGHT returns all of the text. If _num_chars_opt_ is omitted, it is assumed to be 1.
  
## Example

RIGHT ("January 1, 2004", 4)
  
Returns the value 2004.
  