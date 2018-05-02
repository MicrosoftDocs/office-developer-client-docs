---
title: "STRSAMEEX Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251787
 
localization_priority: Normal
ms.assetid: 056b54ae-1475-9480-6ebc-5c34ef48e0f8
description: "Determines whether two strings are the same."
---

# STRSAMEEX Function

Determines whether two strings are the same.
  
## Syntax

STRSAMEEX (" ** *string1* ** ", " ** *string2* ** ", ** *localeID* **, ** *flag* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _string1_ <br/> |Required  <br/> |**String** <br/> |The first string to compare.  <br/> |
| _string2_ <br/> |Required  <br/> |**String** <br/> | The second string to compare.  <br/> |
| _localeID_ <br/> |Required  <br/> |**Numeric** <br/> |The locale ID code.  <br/> |
| _flag_ <br/> |Required  <br/> |**Numeric** <br/> | A bit that specifies the type of comparison.  <br/> |
   
### Return Value

Boolean
  
## Remarks

STRSAMEEX returns TRUE if both input strings are the same and FALSE if they aren't. Use this function to compare multi-byte strings or to do comparisons that use case rules for a specific locale.
  
You can use a combination of any of the following flags with the STRSAMEEX function.
  
|**Flag**|**Description**|
|:-----|:-----|
|1  <br/> |Ignore case.  <br/> |
|2  <br/> |Ignore non-spacing characters.  <br/> |
|4  <br/> |Ignore symbols.  <br/> |
|4096  <br/> |Treat punctuation the same as symbols.  <br/> |
|65536  <br/> |Don't differentiate between Hiragana and Katakana characters.  <br/> |
|131072  <br/> |Don't differentiate between a single-byte character and the same character as a double-byte character.  <br/> |
   

