---
title: "SUBSTITUTE Function" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60115
 
ms.localizationpriority: medium
ms.assetid: 4a27663a-9d37-2ac4-5856-edeb0880f16e
description: "Replaces part of a text string with a different text string."
---

# SUBSTITUTE Function

Replaces part of a text string with a different text string.
  
## Syntax

 SUBSTITUTE (***text***, ***old_text***, ***new_text*** [, ***start_num*** ][, ***ignore_case_opt*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *text* <br/> |Required  <br/> |**String** <br/> | The text or the reference to a cell containing text for which you want to substitute characters. |
| *old_text* <br/> |Required  <br/> |**String** <br/> | The text you want to replace. |
| *new_text* <br/> |Required  <br/> |**String** <br/> | The text you want to use to replace *old_text*. |
| *start_num_opt* <br/> |Optional  <br/> |**Numeric** <br/> |Specifies which occurrences of old_text to replace. |
| *ignore_case_opt* <br/> |Optional  <br/> |**Boolean** <br/> |FALSE if case-sensitive; otherwise, TRUE. The default is FALSE. |

### Return value

String
  
## Remarks

 If you specify *start_num_opt*, only that occurrence of *old_text* is replaced. Otherwise, every occurrence of *old_text* in *text* is changed to *new_text.*
  
Use the SUBSTITUTE function when you want to replace specific text in a text string. If you want to replace text that occurs in a specific location in a text string, use the REPLACE function.
  
## Example

SUBSTITUTE ("1 January 2003", "January", "JAN")
  
Returns "1 JAN 2003".
  
SUBSTITUTE ("1 January 2003","january","JAN")
  
Returns "1 January 2003". No change is made because the text search is case-sensitive.
  