---
title: "USE Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251510
 
localization_priority: Normal
ms.assetid: 410c4187-21f3-d959-750e-9dc6095fba9a
description: "Applies the line pattern, fill pattern, or line end called name to the shape when placed in the LinePattern, FillPattern, BeginArrow, or EndArrow cell."
---

# USE Function

Applies the line pattern, fill pattern, or line end called  _name_ to the shape when placed in the LinePattern, FillPattern, BeginArrow, or EndArrow cell. 
  
## Syntax

USE(" ** *name* ** ") 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _name_ <br/> |Required  <br/> |**String** <br/> |Any string that is a valid master name.  <br/> |
   
### Return value

Number
  
## Remarks

If a master named  _name_ is present on the document stencil of the document, the pattern is applied as a line pattern, fill pattern, begin arrow, or end arrow. 
  
This function always returns 254.
  
## Example

USE("Railroad Tracks") 
  
Formats the shape by applying the master pattern named Railroad Tracks to the shape containing the formula. 
  

