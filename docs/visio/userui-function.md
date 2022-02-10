---
title: "USERUI Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251511
 
ms.localizationpriority: medium
ms.assetid: c01dd938-677c-b2ba-8f56-4638e7e988fd
description: "Evaluates one of the two expressions depending on the value of state."
---

# USERUI Function

Evaluates one of the two expressions depending on the value of  _state_.
  
## Syntax

USERUI(** *state* **, ** *defaultexpression* **, ** *userexpression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _state_ <br/> |Required  <br/> |**Boolean** <br/> |Determines which expression to evaluate. |
| _defaultexpression_ <br/> |Required  <br/> |**String** <br/> |The default expression. |
| _userexpression_ <br/> |Required  <br/> |**String** <br/> |An expression supplied by the user. |
   
## Remarks

If  _state_ is 0, the USERUI function evaluates the  _defaultexpression_. If  _state_ is 1, it evaluates the  _userexpression_.
  
## Example

USERUI(1, if(Width\>6in, 6in, Width), Width\*0.75) 
  
Evaluates the expression Width\*.075 and returns the result. 
  

