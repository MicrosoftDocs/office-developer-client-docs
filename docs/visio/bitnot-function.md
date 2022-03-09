---
title: "BITNOT Function" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251399
 
ms.localizationpriority: medium
ms.assetid: 7b6486bb-3618-3747-4b00-93bd55767c1c
description: "Returns a 16-bit binary number in which each bit is set to 1 only if the corresponding bit in binary number is 0. Otherwise, the bit is set to 0."
---

# BITNOT Function

Returns a 16-bit binary number in which each bit is set to 1 only if the corresponding bit in binary number is 0. Otherwise, the bit is set to 0.
  
## Syntax

BITNOT(***binary number*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *binary number* <br/> |Required  <br/> |**Numeric** <br/> |A 16-bit binary number. |

### Return value

16-bit Binary
  
## Example

BITNOT(6)
  
Returns 65529. The 6 = 0...00110. Therefore, BITNOT(6) = 1...11001.
  