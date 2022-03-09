---
title: "CHAR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251406
 
ms.localizationpriority: medium
ms.assetid: 0803d5d3-d804-5ffe-604d-661b35d1fc01
description: "Returns the ANSI character for a number."
---

# CHAR Function

Returns the ANSI character for a number.
  
## Syntax

CHAR(***number*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *number* <br/> |Required  <br/> |**Number** <br/> |The number whose ANSI character you want to get. |

## Remarks

The resulting string is one character in length. The *number* parameter must be an integer between 1 and 255 (inclusive), or the function returns an error.
  
## Example

CHAR(9)
  
Returns the tab character.
  