---
title: "FIND Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60101
 
ms.localizationpriority: medium
ms.assetid: c827ecd4-5593-6d4f-2746-d13b02b098fe
description: "Finds one text string contained within another text string, and returns the starting position of the text string you are seeking relative to its position in the text string that contains it."
---

# FIND Function

Finds one text string contained within another text string, and returns the starting position of the text string you are seeking relative to its position in the text string that contains it.
  
## Syntax

FIND (** *find_text* **, ** *within_text* **,[ ** *start_num* ** ], [ ** *ignore_case* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _find_text_ <br/> |Required  <br/> |**String** <br/> |The text string you want to find. |
| _format_ <br/> |Required  <br/> |**String** <br/> |The text string that contains the text you want to find. |
| _start_num_ <br/> |Optional  <br/> |**Number** <br/> |The character at which to start the search. The first character in  _within_text_ is 1. If  _start_num_ is missing, it is assumed to be 1. |
| _ignore_case_ <br/> |Optional  <br/> |**Boolean** <br/> |By default, the FIND function is case-sensitive. If you want the FIND function to ignore case, set this argument to TRUE. |
   
### Return value

Number
  
## Remarks

If multiple matches are found, the FIND function returns the starting position of the first match in the string. The  _find_text_ argument does not consider any characters to be wildcards. 
  
If  _find_text_:
  
-  Is empty (""), FIND matches the first character in the search string (that is, the character numbered  _start_num_ or 1). 
    
- Does not appear in  _within_text_, FIND returns the #VALUE! error value. 
    
If  _start_num_:
  
- Is not greater than zero (0), FIND returns the #VALUE! error value. 
    
- Is greater than the length of  _within_text_, FINDreturns the #VALUE! error value. 
    
## Example

FIND ("2003","January 1, 2003") 
  
Returns 12. 
  

