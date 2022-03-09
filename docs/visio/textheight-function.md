---
title: "TEXTHEIGHT Function" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251504
 
ms.localizationpriority: medium
ms.assetid: 5a10892f-c8fa-c127-2f5a-564009ce5411
description: "Returns the height of the composed text in a shape where no text line exceeds maximumwidth."
---

# TEXTHEIGHT Function

Returns the height of the composed text in a shape where no text line exceeds _maximumwidth_.
  
## Syntax

TEXTHEIGHT(***shapename!TheText*** ***[,maximumwidth]***)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _shapename!theText_ <br/> |Required  <br/> |**String** <br/> |A reference to the cell named TheText in the target shape. _shapename!_ is the name of the shape from which you want to retrieve the text. |
| _maximumwidth_ <br/> |Optional  <br/> |**Numeric** <br/> |The maximum width of the text block. |

### Return value

String
  
## Remarks

The returned value includes the height of the text including the space before and after text, the line spacing in text, and the top and bottom text block margins. This function is commonly used to adjust the height of a shape to fit the text it contains.
  
## Example

TEXTHEIGHT(TheText,(Width - 0.5 in))
  
Returns the height of the text when wrapped to the width of the shape minus 0.5 inches.
  