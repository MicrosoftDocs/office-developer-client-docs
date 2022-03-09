---
title: "UNICHAR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60117
 
ms.localizationpriority: medium
ms.assetid: 371a475d-50f7-6b4c-4b47-581cd778dcba
description: "Returns the Unicode character from a number."
---

# UNICHAR Function

Returns the Unicode character from a number.
  
## Syntax

UNICHAR (***number***)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *number* <br/> |Required  <br/> |**Integer** <br/> |An integer between 1 and 65,535 (inclusive), or the function returns an error. |

## Remarks

The resulting string is one Unicode character (two characters) in length.
  
## Example

UNICHAR(65)
  
Returns A (Latin Capital Letter A)
  