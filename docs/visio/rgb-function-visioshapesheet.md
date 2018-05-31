---
title: "RGB Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251489
 
localization_priority: Normal
ms.assetid: f6b9f65c-6752-16cb-7eb1-44e1ce56e80b
description: "Returns a value representing an index in the document's color palette. It specifies a color by its red, green, and blue components, where each is a number in the range 0 to 255, inclusive, or an expression that evaluates to such a number."
---

# RGB Function (VisioShapeSheet)

Returns a value representing an index in the document's color palette. It specifies a color by its red, green, and blue components, where each is a number in the range 0 to 255, inclusive, or an expression that evaluates to such a number. 
  
## Syntax

RGB(** *red* **, ** *green* **, ** *blue* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _red_ <br/> |Required  <br/> |**Number** <br/> |The red component.  <br/> |
| _green_ <br/> |Required  <br/> |**Number** <br/> |The green component.  <br/> |
| _blue_ <br/> |Required  <br/> |**Nmber** <br/> |The blue component.  <br/> |
   
### Return value

Number
  
## Remarks

If the color returned by the function does not already exist in the current document's color palette, it is added to the palette.
  
The following table lists some standard colors and their red, green, and blue values.
  
|**Color**|**Red value**|**Green value**|**Blue value**|
|:-----|:-----|:-----|:-----|
|Black  <br/> |0  <br/> |0  <br/> |0  <br/> |
|Blue  <br/> |0  <br/> |0  <br/> |255  <br/> |
|Green  <br/> |0  <br/> |255  <br/> |0  <br/> |
|Cyan  <br/> |0  <br/> |255  <br/> |255  <br/> |
|Red  <br/> |255  <br/> |0  <br/> |0  <br/> |
|Magenta  <br/> |255  <br/> |0  <br/> |255  <br/> |
|Yellow  <br/> |255  <br/> |255  <br/> |0  <br/> |
|White  <br/> |255  <br/> |255  <br/> |255  <br/> |
   
## Example 1

RGB(0,0,255)
  
Returns the index for the color blue.
  
## Example 2

RGB(RED(Sheet.1!FillForegnd),120,0)
  
Returns the index for a color whose red component mirrors Sheet.1's fill foreground.
  

