---
title: "IF Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251442
 
ms.localizationpriority: medium
ms.assetid: 66771ad3-0fb3-68ff-81da-d1162d37c05a
description: "Returns valueiftrue if logicalexpression is TRUE. Otherwise, it returns valueiffalse."
---

# IF Function

Returns _valueiftrue_ if _logicalexpression_ is TRUE. Otherwise, it returns _valueiffalse_.
  
## Syntax

IF(***logicalexpression***, ***valueiftrue***, ***valueiffalse*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _logicalexpression_ <br/> |Required  <br/> |**String** <br/> |Expression to evaluate. |
| _valueiftrue_ <br/> |Required  <br/> |**Varies** <br/> |Value to return if _logicalexpression_ is true. |
| _valueiffalse_ <br/> |Required  <br/> |**Varies** <br/> | Value to return if _logicalexpression_ is false. |

### Return value

Varies
  
## Example

IF(Height \> 1.25 in,5,7)
  
Returns 5 if the shape's height is greater than 1.25 inches. Returns 7 if the shape's height is less than or equal to 1.25 inches.
  