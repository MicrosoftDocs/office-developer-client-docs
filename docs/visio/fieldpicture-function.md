---
title: "FIELDPICTURE Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251592
 
ms.localizationpriority: medium
ms.assetid: df88c55f-c098-dd4c-bf53-c7d7b60cf719
description: "Returns a format-picture string that matches the Microsoft Visio internal text field format code."
---

# FIELDPICTURE Function

Returns a format-picture string that matches the Microsoft Visio internal text field format code.
  
## Syntax

FIELDPICTURE(**code*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *code* <br/> |Required  <br/> |**Number** <br/> | A text field format code. |

### Return value

String
  
## Remarks

Format picture strings are used in the FORMAT function to define the expansion of values to dates, times, numbers, and unit labels.
  
## Example

FIELDPICTURE(0)
  
Returns the format picture string "esc(0)", which specifies a number that has one decimal place and a lowercase unit description when used in the FORMAT function.
  