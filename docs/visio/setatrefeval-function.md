---
title: "SETATREFEVAL Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1042150
 
localization_priority: Normal
ms.assetid: b3f3a0a0-7b14-0b71-d247-ada81b93b66b
description: "Used in the set_expression parameter of the SETATREF function to indicate that set_expression should be evaluated before assigning to the reference parameter in SETATREF."
---

# SETATREFEVAL Function

Used in the  _set_expression_ parameter of the SETATREF function to indicate that  _set_expression_ should be evaluated before assigning to the  _reference_ parameter in SETATREF. 
  
## Syntax

SETATREFEVAL( ** *expr* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expr_ <br/> |Required  <br/> |**Varies** <br/> | An expression that is evaluated when the SETATREF function redirects  _set_expression_ to another cell.  <br/> |
   
## Remarks

When assigning the  *set_expression*  parameter of the SETATREF function to a referenced cell, Microsoft Visio writes  *set_expression*  to the cell as an expression by default. However, if any portion of the  *set_expression*  parameter is wrapped by the SETATREFEVAL function, Visio evaluates the expression and replaces the SETATREFEVAL function with its result prior to resolving the SETATREF expression. 
  
## Example

For an example, see the [SETATREF](setatref-function.md) function. 
  

