---
title: "MAGNITUDE Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251461
 
localization_priority: Normal
ms.assetid: 9f443687-9861-5f51-94c4-f056805f736b
description: "Returns the magnitude of the vector whose rise is A and whose run is B, multiplied by the respective constants constantA and constantB."
---

# MAGNITUDE Function

Returns the magnitude of the vector whose rise is  _A_ and whose run is  _B_, multiplied by the respective constants  _constantA_ and  _constantB_. 
  
## Syntax

MAGNITUDE(** *constantA* **, ** *A* **, ** *constantB* **, ** *B* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _constantA_ <br/> |Required  <br/> |**Number** <br/> |The constant by which to multiply the rise.  <br/> |
| _A_ <br/> |Required  <br/> |**Number** <br/> |The rise.  <br/> |
| _constantB_ <br/> |Required  <br/> |**Number** <br/> |The constant by which to multiply the run.  <br/> |
| _B_ <br/> |Required  <br/> |**Number** <br/> |The run.  <br/> |
   
## Remarks

MAGNITUDE is calculated according to the following formula:
  
SQRT((constantA \* A)^2 + (constantB \* B)^2)
  
## Example

MAGNITUDE(1, 3, 1, 4) 
  
Returns 5. 
  

