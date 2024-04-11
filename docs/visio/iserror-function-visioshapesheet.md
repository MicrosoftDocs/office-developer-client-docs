---
title: "ISERROR Function (VisioShapeSheet)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251452
 
ms.localizationpriority: medium
ms.assetid: 4864ebc2-fee6-2415-7c59-e0af8611f8d6
description: "Returns TRUE if the value of cellreference is any error type; otherwise, it returns FALSE. The ISERROR function is used in formulas that refer to another cell."
---

# ISERROR Function (VisioShapeSheet)

Returns TRUE if the value of _cellreference_ is any error type; otherwise, it returns FALSE. The ISERROR function is used in formulas that refer to another cell.
  
## Syntax

ISERROR(***cellreference*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellreference_ <br/> |Required  <br/> |**String** <br/> |Reference to a cell. |

## Example 1

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.A1  <br/> |=NA( )  <br/> |#N/A!  <br/> |
|Scratch.B1  <br/> |=ISERROR(Scratch.A1)  <br/> |TRUE  <br/> |

Returns TRUE because the #N/A! error is recognized by the ISERROR function. You can use ISERR to find all types but the #N/A! error.
  
## Example 2

|**Cell**|**Formula**|**Value returned**|
|:-----|:-----|:-----|
|Scratch.X1  <br/> |="House"  <br/> |#VALUE!  <br/> |
|Scratch.B1  <br/> |=ISERROR(Scratch.X1)  <br/> |TRUE  <br/> |

Returns TRUE because the #VALUE! error is recognized by the ISERROR function. To build an expression based on the #VALUE! error, use the ISERRVALUE function.
  