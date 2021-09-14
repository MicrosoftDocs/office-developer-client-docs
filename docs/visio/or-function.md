---
title: "OR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251476
 
ms.localizationpriority: medium
ms.assetid: 6c2154fa-4190-0699-61f7-f2bdf87173ec
description: "Returns TRUE (1) if any of the logical expressions passed as parameters are TRUE."
---

# OR Function

Returns TRUE (1) if any of the logical expressions passed as parameters are TRUE.
  
## Syntax

OR(** *logicalexpression1* **, ** *logicalexpression2* **,..., ** *logicalexpressionN* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _logicalexpression1_ <br/> |Required  <br/> |**String** <br/> |The first expression whose truth you want to evaluate.  <br/> |
| _logicalexpression2_ <br/> |Required  <br/> |**String** <br/> |The second expression whose truth you want to evaluate.  <br/> |
| _logicalexpressionN_ <br/> |Required  <br/> |**String** <br/> |The Nth expression whose truth you want to evaluate.  <br/> |
   
### Return value

Boolean
  
## Remarks

Any expression that evaluates to a non-zero value is considered TRUE. If all of the logical expressions are FALSE or equal 0, this function returns FALSE. 
  
## Example

OR(Height \> 1,PinX \> 1) 
  
Returns TRUE (1) if either expression is TRUE. Returns FALSE (0) only if both expressions are FALSE. 
  

