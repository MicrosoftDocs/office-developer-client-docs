---
title: "REPT Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1027335
 
localization_priority: Normal
ms.assetid: 53362a32-ac27-42a3-ace1-c6184ab20b52
description: "Repeats text a given number of times."
---

# REPT Function

Repeats text a given number of times. 
  
## Syntax

REPT (** *text* **, ** *number_times* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _text_ <br/> |Required  <br/> |**String** <br/> | The text you want to repeat.  <br/> |
| _number_times_ <br/> |Required  <br/> |**Number** <br/> |A positive number specifying the number of times to repeat text.  <br/> |
   
## Remarks

If  *number_times*  is: 
  
- Zero (0), REPT returns "" (empty text).
    
- Not an interger, it is truncated.
    
## Example

REPT ("\*", 5) 
  
Returns \*\*\*\*\*. 
  

