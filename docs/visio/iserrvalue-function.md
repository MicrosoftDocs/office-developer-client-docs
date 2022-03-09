---
title: "ISERRVALUE Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251453
 
ms.localizationpriority: medium
ms.assetid: c7feec6f-f47a-60ee-b056-7b2dc51ed9a9
description: "Returns TRUE if the value of cellreference is error type #VALUE, where an argument in the formula is the wrong type. The ISERRVALUE function is used in logical expressions that refer to another cell."
---

# ISERRVALUE Function

Returns TRUE if the value of _cellreference_ is error type #VALUE, where an argument in the formula is the wrong type. The ISERRVALUE function is used in logical expressions that refer to another cell.
  
## Syntax

ISERRVALUE(**_cellreference_** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellreference_ <br/> |Required  <br/> |**String** <br/> |Reference to a cell. |

## Remarks

Scratch cells A through D won't return a #VALUE! error because the formula can contain numbers and letters in the same string. Cells X and Y must contain numbers only.
  
## Example 1

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.X1  <br/> |= "House"  <br/> |#VALUE!  <br/> |
|Scratch.A1  <br/> |= If (ISERRVALUE(Scratch.X1),2,Scratch.X1)  <br/> |2  <br/> |

Returns 2 because the value returned is a #VALUE! error, and the expression instructs Microsoft Visio to return a 2 in place of the error.
  
## Example 2

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.A1  <br/> |="5 + 7"  <br/> |5 + 7  <br/> |
|Scratch.B1  <br/> |=If (ISERRVALUE(Scratch.A1),2,Scratch.A1)  <br/> |5 + 7  <br/> |

Returns 12 because the value returned is not a #VALUE! error, and the expression instructs Visio to return the value of the original cell.
  