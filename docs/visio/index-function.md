---
title: "INDEX Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251443
 
ms.localizationpriority: medium
ms.assetid: cc46f91e-733f-e25a-17d2-19df8c8febd2
description: "Returns the substring at the zero-based location index in the list delimited by delimiter. Or, if the index is out of range, returns an empty string or the optional token provided as the errorvalue argument."
---

# INDEX Function

Returns the substring at the zero-based location _index_ in the _list_ delimited by _delimiter_. Or, if the index is out of range, returns an empty string or the optional token provided as the _errorvalue_ argument.
  
## Syntax

INDEX(***index***," **_list_** "[,[ **_delimiter_** ][,[ **_errorvalue_** ]]])
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _index_ <br/> |Required  <br/> |**Number** <br/> |The location that you want to find. |
| _list_ <br/> |Required  <br/> |**String** <br/> |The list in which you want to search. |
| _delimiter_ <br/> |Optional  <br/> |**String** <br/> | The string to use as a delimiter within _list_. A _delimiter_ string can be more than one character in length and include multibyte characters. The default is a semicolon. |
| _errorvalue_ <br/> |Optional  <br/> |**Number** <br/> | A user-specified value to return if the index is out of range. The default is an empty string. |

## Remarks

If the list begins or ends with a delimiter, a null string is assumed to exist before or after the list. Consecutive delimiters imply a null string in between.
  
If the index is out of range, Visio returns an empty string or the optional token provided as the _errorvalue_ argument.
  
## Example 1

INDEX(3,"cat;rat;;goat")
  
Returns "goat".
  
## Example 2

INDEX(54,";1;2;3;",,"ERROR")
  
Returns "ERROR".
  