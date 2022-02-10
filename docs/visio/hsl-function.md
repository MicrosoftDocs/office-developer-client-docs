---
title: "HSL Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251438
 
ms.localizationpriority: medium
ms.assetid: c9314c39-1d2e-a18f-c01b-8817286099dc
description: "Returns a value representing an index in the document's color palette. It specifies a color by its hue, saturation, and luminosity components."
---

# HSL Function

Returns a value representing an index in the document's color palette. It specifies a color by its hue, saturation, and luminosity components.
  
## Syntax

HSL(** *hue* **, ** *saturation* **, ** *luminosity* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _hue_ <br/> |Required  <br/> |**Number** <br/> |The color's hue, expressed as a number in the range 0 to 239, inclusive, or an expression that evaluates to such a number. |
| _saturation_ <br/> |Required  <br/> |**Number** <br/> |The color's saturation, expressed as a number in the range 0 to 240, inclusive, or an expression that evaluates to such a number. |
| _luminosity_ <br/> |Required  <br/> |**Number** <br/> | The color's luminosity, expressed as a number in the range 0 to 240, inclusive, or an expression that evaluates to such a number. |
   
### Return value

Number
  
## Remarks

If the color returned by the function does not already exist in the current document's color palette, it is added to the document's list of available colors. 
  
The following table lists some standard colors and their hue, saturation, and luminosity values. 
  
|**Color**|**Hue value**|**Saturation value**|**Luminosity value**|
|:-----|:-----|:-----|:-----|
|Black  <br/> |0  <br/> |0  <br/> |24  <br/> |
|Blue  <br/> |160  <br/> |240  <br/> |120  <br/> |
|Green  <br/> |80  <br/> |240  <br/> |120  <br/> |
|Cyan  <br/> |120  <br/> |240  <br/> |120  <br/> |
|Red  <br/> |0  <br/> |240  <br/> |120  <br/> |
|Magenta  <br/> |200  <br/> |240  <br/> |120  <br/> |
|Yellow  <br/> |40  <br/> |240  <br/> |120  <br/> |
|White  <br/> |0  <br/> |0  <br/> |240  <br/> |
   
## Example 1

HSL(160,240,120)
  
Returns the index for the color blue.
  
## Example 2

HSL(HUE(FillForegnd),SAT(FillForegnd),MIN(LUM(FillForegnd)+100,240))
  
Returns the index for a color that mirrors the fill foreground color with increased luminosity.
  

