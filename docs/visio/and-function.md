---
title: "AND Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251391
 
localization_priority: Normal
ms.assetid: 434d7ceb-1050-c667-fb3d-b6634440c18e
description: "Returns TRUE (1) if all of the logical expressions supplied are TRUE. If any of the logical expressions are FALSE or 0, the AND function returns FALSE (0)."
---

# AND Function

Returns TRUE (1) if all of the logical expressions supplied are TRUE. If any of the logical expressions are FALSE or 0, the AND function returns FALSE (0).
  
## Syntax

AND( ** *logical expression1* **, ** *logical expression2* **,..., ** *logical expressionN* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _logical expression_ <br/> |Required  <br/> |**String** <br/> | A combination of constants, operators, functions, and references to ShapeSheet cells that results in a value. Any expression that evaluates to a non-zero value is considered to be TRUE.  <br/> |
   
## Example

AND(Height \> 1, PinX \> 1)
  
Returns TRUE if both expressions are TRUE. Returns FALSE if either expression is FALSE.
  

