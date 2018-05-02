---
title: "THEMECBV Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: ef62f63f-b2ce-4d12-a294-93dbdc9a869d
description: "Returns an RGB value or an integer that represents an index in the document's color palette, where the color (number) passed in as an argument has been modified by the specified tint or shade value stored in the gradient settings of the active theme."
---

# THEMECBV Function

Returns an RGB value or an integer that represents an index in the document's color palette, where the color (number) passed in as an argument has been modified by the specified tint or shade value stored in the gradient settings of the active theme. 
  
## Version Information

Version Added: Visio 2013 
  
## Syntax

 **THEMECBV**( _color_,  _gradient_stop_number_)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _color_ <br/> |Required  <br/> |**Number** <br/> |A number representing an index in the document's color palette.  <br/> |
| _gradient_stop_number_ <br/> |Required  <br/> |**Number** <br/> |The gradient stop (tint or shade) stored in the gradient settings of the active theme to apply to the color.  <br/> |
   
## Return Value

 **Number**
  
## Remarks

> [!NOTE]
> The THEMECBV function does nothing to the color passed in as an argument if the QuickStyle that is assigned to the shape does not have a gradient. 
  
The gradient settings in a theme are a series of numbered gradient stops that correspond to a "lightening" (tint) or "darkening" (shade). These shades and tints are applied to a base color to create a gradient color effect.
  
The **THEMECBV** function takes a color input and outputs the color after it has been modified by the tint or shade of the specified gradient stop. The tints and shades come from the theme's definition, if the current quick style contains a gradient fill. If the active Quick Style does not specify a gradient fill or the shape is set to No Theme, then this formula simply returns the color that was passed in for the first argument. 
  
## Example

 `THEMECBV(FillForegnd, 5)`
  
Returns the color created by applying the tint or shade in the fifth gradient stop of the gradient to the color specified in the **FillForegnd** cell. 
  
 `THEMECBV(RGB(255,0,0), 2)`
  
Returns a shade or tint of red created by applying the second gradient stop to a base color of red.
  

