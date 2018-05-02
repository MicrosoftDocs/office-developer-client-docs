---
title: "LOOKUP Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251457
 
localization_priority: Normal
ms.assetid: cb6ec664-6062-75d0-1514-8058b98c2c36
description: "Returns a zero-based index that indicates the location of the substring key in a list, or returns -1 if the target string contains the delimiter."
---

# LOOKUP Function

Returns a zero-based index that indicates the location of the substring  _key_ in a  _list_, or returns -1 if the target string contains the  _delimiter_.
  
## Syntax

LOOKUP(" ** *key* ** "," ** *list* ** "[," ** *delimiter* ** "]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _key_ <br/> |Required  <br/> |**String** <br/> |The string that you want to look up.  <br/> |
| _list_ <br/> |Required  <br/> |**String** <br/> | The list in which you want to search.  <br/> |
| _delimiter_ <br/> |Optional  <br/> |**String** <br/> | The string to use as a delimiter within  _list_. A  _delimiter_ string can be more than one character in length and may include multibyte characters. The default is a semicolon.  <br/> |
   
### Return Value

Numeric
  
## Remarks

The LOOKUP function uses a case-insensitive search. If the list begins or ends with a delimiter, a null string is assumed to exist before or after the list. Consecutive delimiters imply a null string in between. 
  
All the arguments must be strings or expressions that can be converted to strings. If they are not, an empty string is substituted for the offending argument. 
  
## Example 1

LOOKUP("rat","cat;rat;;goat")
  
Returns 1.
  
## Example 2

LOOKUP("",";cat;rat;;goat")
  
Returns 0.
  
## Example 3

LOOKUP("t","cat;rat;;goat","a")
  
Returns 3.
  

