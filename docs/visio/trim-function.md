---
title: "TRIM Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1027318
 
localization_priority: Normal
ms.assetid: 6f2d84fd-27eb-4c2f-a2e1-43d20e0c78be
description: "Removes all space from text, except for single spaces between words."
---

# TRIM Function

Removes all space from text, except for single spaces between words. 
  
## Syntax

TRIM ( ** *text* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _text_ <br/> |Required  <br/> |**String** <br/> |The text from which you want to remove spaces.  <br/> |
   
### Return value

String
  
## Remarks

You can use the TRIM function on text that you have received from another application that may have irregular spacing.
  
## Example

TRIM ("January 1, 2003 ") 
  
Returns "January 1, 2003". 
  

