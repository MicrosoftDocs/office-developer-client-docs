---
title: "UNICHAR Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60117
 
localization_priority: Normal
ms.assetid: 371a475d-50f7-6b4c-4b47-581cd778dcba
description: "Returns the Unicode character from a number."
---

# UNICHAR Function

Returns the Unicode character from a number. 
  
## Syntax

UNICHAR (** *number* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Integer** <br/> |An integer between 1 and 65,535 (inclusive), or the function returns an error.  <br/> |
   
## Remarks

The resulting string is one Unicode character (two characters) in length. 
  
## Example

UNICHAR(65) 
  
Returns A (Latin Capital Letter A) 
  

