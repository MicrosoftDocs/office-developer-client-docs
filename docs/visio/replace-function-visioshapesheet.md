---
title: "REPLACE Function (VisioShapeSheet)" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60108
 
ms.localizationpriority: medium
ms.assetid: 70c9fc1d-6e7b-479f-effd-0d4bc8ae0f72
description: "Replaces part of a text string, based on the number of characters you specify, with a different text string."
---

# REPLACE Function (VisioShapeSheet)

Replaces part of a text string, based on the number of characters you specify, with a different text string.
  
## Syntax

REPLACE (***old_text***, ***start_num***, ***num_chars***, ***new_text*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *old_text* <br/> |Required  <br/> |**String** <br/> |The text in which you want to replace some characters. |
| *start_num* <br/> |Required  <br/> |**Number** <br/> |The position of the character in *old_text* that you want to replace with *new_text*. The first character in the string is position 1. |
| *num_chars* <br/> |Required  <br/> |**Number** <br/> |The number of characters in *old_text* that you want to replace  <br/> |
| *new_text* <br/> |Required  <br/> |**String** <br/> |The text that will replace characters in *old_text*. |

### Return value

String
  
## Remarks

Use the REPLACE function when you want to replace text that occurs in a specific location in a text string. If you want to replace specific text in a text string, use the SUBSTITUTE function.
  
## Example

REPLACE ("01/03/2002",9,2,"03")
  
Returns 01/03/2003.
  