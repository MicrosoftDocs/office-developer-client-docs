---
title: "BITXOR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251401
 
ms.localizationpriority: medium
ms.assetid: 672eacaf-a374-c7e2-b39b-8d42d2371aee
description: "Returns a 16-bit binary number in which each bit is set to 1 if the corresponding bit in either but not both binary number1 and binary number2 is 1. Otherwise, the bit is set to 0."
---

# BITXOR Function

Returns a 16-bit binary number in which each bit is set to 1 if the corresponding bit in either but not both binary number1 and binary number2 is 1. Otherwise, the bit is set to 0.
  
## Syntax

BITXOR(***binary number1***, ***binary number2*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *binary number1* <br/> |Required  <br/> |**Numeric** <br/> |The first 16-bit binary number. |
| *binary number2* <br/> |Required  <br/> |**Numeric** <br/> |The second 16-bit binary number. |

### Return value

16-bit Binary
  
## Example

BITXOR(12,6)
  
Returns 10. The 12 = 0...01100. The 6 = 0...00110. Therefore, BITXOR(12,6) = 0...01010.
  