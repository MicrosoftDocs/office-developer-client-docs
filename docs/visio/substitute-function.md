---
title: "SUBSTITUTE Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60115
 
localization_priority: Normal
ms.assetid: 4a27663a-9d37-2ac4-5856-edeb0880f16e
description: "Replaces part of a text string with a different text string."
---

# SUBSTITUTE Function

Replaces part of a text string with a different text string. 
  
## Syntax

 SUBSTITUTE (** *text* **, ** *old_text* **, ** *new_text* ** [, ** *start_num* ** ][, ** *ignore_case_opt* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _text_ <br/> |Required  <br/> |**String** <br/> | The text or the reference to a cell containing text for which you want to substitute characters.  <br/> |
| _old_text_ <br/> |Required  <br/> |**String** <br/> | The text you want to replace.  <br/> |
| _new_text_ <br/> |Required  <br/> |**String** <br/> | The text you want to use to replace  _old_text_.  <br/> |
| _start_num_opt_ <br/> |Optional  <br/> |**Numeric** <br/> |Specifies which occurrences of old_text to replace.  <br/> |
| _ignore_case_opt_ <br/> |Optional  <br/> |**Boolean** <br/> |FALSE if case-sensitive; otherwise, TRUE. The default is FALSE.  <br/> |
   
### Return value

String
  
## Remarks

 If you specify  _start_num_opt_, only that occurrence of  _old_text_ is replaced. Otherwise, every occurrence of  _old_text_ in  _text_ is changed to  _new_text._
  
Use the SUBSTITUTE function when you want to replace specific text in a text string. If you want to replace text that occurs in a specific location in a text string, use the REPLACE function.
  
## Example

SUBSTITUTE ("1 January 2003", "January", "JAN") 
  
Returns "1 JAN 2003". 
  
SUBSTITUTE ("1 January 2003","january","JAN") 
  
Returns "1 January 2003". No change is made because the text search is case-sensitive. 
  

