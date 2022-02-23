---
title: "ROUND Function (VisioShapeSheet)" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251491
 
ms.localizationpriority: medium
ms.assetid: a374fe7d-7302-5365-81ab-64f5474d9d5c
description: "Rounds a number to the precision represented by numberofdigits."
---

# ROUND Function (VisioShapeSheet)

Rounds a number to the precision represented by *numberofdigits*.
  
## Syntax

ROUND(***number***, ***numberofdigits*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *number* <br/> |Required  <br/> |**Number** <br/> |The number to round off. |
| *numberofdigits* <br/> |Required  <br/> |**Number** <br/> |The number of decimal places of precision. |

## Remarks

If *numberofdigits* is greater than 0, *number* is rounded by *numberofdigits* to the right of the decimal. If *numberofdigits* is 0, *number* is rounded to an integer. If *numberofdigits* is less than 0, *number* is rounded by *numberofdigits* to the left of the decimal.
  
## Example 1

ROUND(123.654,2)
  
Returns 123.65.
  
## Example 2

ROUND(123.654,0)
  
Returns 124.
  
## Example 3

ROUND(123.654,-1)
  
Returns 120.
  