---
title: "LEFT Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1021757
 
ms.localizationpriority: medium
ms.assetid: 0c2f6e06-b772-2006-ec7b-8695d097f146
description: "Returns the left-most character or characters in a text string, based on the number of characters you specify."
---

# LEFT Function (VisioShapeSheet)

Returns the left-most character or characters in a text string, based on the number of characters you specify.
  
## Syntax

LEFT(***text***, [, ***num_chars_opt*** ])
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *text* <br/> |Required  <br/> |**String** <br/> |The text string that contains the characters you want to extract. |
| *num_chars_opt* <br/> |Optional  <br/> |**Numeric** <br/> |The number of characters you want to extract. |

### Return value

String
  
## Remarks

The value of *num_chars_opt* must be greater than or equal to zero (0).
  
If *num_chars_opt* is greater than the length of the text, LEFT returns all of the text. If *num_chars_opt* is omitted, it is assumed to be 1.
  
## Example

LEFT ("January 1, 2004", 3)
  
Returns the value "Jan".
  