---
title: "BITAND Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251398
 
localization_priority: Normal
ms.assetid: c437de23-d2e0-469d-62e6-8eb8b8cfea5c
description: "Returns a 16-bit binary number in which each bit is set to 1 only if the corresponding bit in both binarynumber1 and binarynumber2 is 1. Otherwise, the bit is set to 0."
---

# BITAND Function

Returns a 16-bit binary number in which each bit is set to 1 only if the corresponding bit in both binarynumber1 and binarynumber2 is 1. Otherwise, the bit is set to 0. 
  
## Syntax

BITAND(** *binarynumber1* **, ** *binarynumber2* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _binary number1_ <br/> |Required  <br/> |**Numeric** <br/> |The first 16-bit binary number.  <br/> |
| _binary number2_ <br/> |Required  <br/> |**Numeric** <br/> |The second 16-bit binary number.  <br/> |
   
## Remarks

You can use this function to test and change properties of a shape that are stored as bitmasks, for example, the shape's text format.
  
## Example

BITAND(12,6)
  
Returns 4. The 12 = 0...01100. The 6 = 0...00110. Therefore, BITAND(12,6) = 0...00100.
  

