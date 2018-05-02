---
title: "LOWER Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251459
 
localization_priority: Normal
ms.assetid: 1d198ea6-49e0-e462-b2cf-b65fbb920b55
description: "Returns a string converted to lowercase."
---

# LOWER Function

Returns a string converted to lowercase.
  
## Syntax

LOWER( ** *expression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**Varies** <br/> | A string, a cell reference, or an expression; the result is converted to a string which is then converted to lowercase.  <br/> |
   
### Return Value

String
  
## Remarks

The case conversion is locale-specific, based on the current user settings. 
  
## Example

LOWER("mIxEd CAse") 
  
Returns "mixed case". 
  

