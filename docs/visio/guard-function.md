---
title: "GUARD Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251435
 
localization_priority: Normal
ms.assetid: 6c85414c-9fb6-cdc5-f5b6-8eb13c9608af
description: "Protects expression from deletion and change by actions performed in the drawing window, for example, moving, sizing, grouping, or ungrouping shapes."
---

# GUARD Function

Protects  *expression*  from deletion and change by actions performed in the drawing window, for example, moving, sizing, grouping, or ungrouping shapes. 
  
## Syntax

GUARD( ** *expression* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**String** <br/> |A combination of constants, operators, functions, and references to ShapeSheet cells that results in a value.  <br/> |
   
## Remarks

The cells most often affected by the GUARD function are Width, Height, PinX, and PinY. 
  
Guarding a formula in any cell prevents that cell's value from being changed by actions in the drawing window. However, one action in the drawing window can affect several cells, and each of these cells must be guarded if you want to prevent unexpected changes to the shape's appearance. 
  
## Example

GUARD(TEXTWIDTH(TheText) + 0.5 in) 
  
This expression in the Width cell of a shape's Shape Transform section prevents the expression (TEXTWIDTH(TheText) + 0.5 in) from being replaced with another value when the shape's width is changed in the drawing window. TheText is a cell that gets triggered when the associated shape's text composition changes. 
  

