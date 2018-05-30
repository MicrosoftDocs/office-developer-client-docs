---
title: "STRSAME Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251786
 
localization_priority: Normal
ms.assetid: d9fc2007-cc21-b20c-adee-be87cc356753
description: "Determines whether strings are the same. It returns TRUE if they are the same and FALSE if they aren't."
---

# STRSAME Function

Determines whether strings are the same. It returns TRUE if they are the same and FALSE if they aren't. 
  
## Syntax

STRSAME (" ** *string1* ** ", " ** *string2* ** ", ** *ignoreCase* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _string1_ <br/> |Required  <br/> |**String** <br/> |The first string to compare.  <br/> |
| _string2_ <br/> |Required  <br/> |**String** <br/> |The second string to compare.  <br/> |
| _ignoreCase_ <br/> |Optional  <br/> |**Boolean** <br/> |TRUE to ignore the case and FALSE to compare the case. The default is FALSE.  <br/> |
   
### Return value

Boolean
  
## Remarks

To compare multi-byte strings or to do comparisons using case rules for a specific locale, use the STRSAMEEX function.
  
## Example 1

STRSAME("cat","dog")
  
Returns FALSE.
  
## Example 2

STRSAME("cat","cat")
  
Returns TRUE.
  
## Example 3

STRSAME("cat","cat", TRUE)
  
Returns TRUE.
  
## Example 4

STRSAME("cat","CAT")
  
Returns FALSE.
  
## Example 5

STRSAME("cat","CAT", TRUE)
  
Returns TRUE.
  
## Example 6

STRSAME("cät,"CAT", TRUE)
  
Returns FALSE.
  
## Example 7

STRSAME("cät,"CÄT", TRUE)
  
Returns TRUE.
  

