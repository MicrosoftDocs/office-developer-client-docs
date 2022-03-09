---
title: "EVALTEXT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251422
 
ms.localizationpriority: medium
ms.assetid: c9b5b96c-d8c8-6119-e3f1-a2ce9d7c043e
description: "Evaluates the text in shapename as if it were a formula and returns the result."
---

# EVALTEXT Function

Evaluates the text in _shapename_ as if it were a formula and returns the result.
  
## Syntax

EVALTEXT(***shapename!theText*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _shapename!theText_ <br/> |Required  <br/> |**String** <br/> |A cell that is triggered when the associated shape's text composition changes. |

### Return value

String
  
## Remarks

 _shapename_ can be used to refer to the text of a shape other than the current shape.
  
If there is no text, the result is zero. If the text cannot be evaluated, the function returns an error.
  
## Example

EVALTEXT(Line.2!theText)
  
Evaluates the text contained in the shape Line.2. For example, if Line.2 contains "4 ft + 0.5 ft", returns the value 4.5 ft.
  