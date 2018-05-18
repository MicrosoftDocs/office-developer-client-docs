---
title: "TONE Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: c2d6a7dd-9f15-27bd-9623-2a047683ff98
description: "Modifies the color by decreasing its saturation by the amount specified in the int parameter."
---

# TONE Function

Modifies the color by decreasing its saturation by the amount specified in the  _int_ parameter. 
  
## Syntax

TONE( ** *color* **, ** *int* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _color_ <br/> |Required  <br/> |**Numeric** <br/> |The Microsoft Visio color index or RGB value of the color.  <br/> |
| _int_ <br/> |Required  <br/> |**Integer** <br/> |The amount by which to decrease the saturation of the color. Can be positive or negative.  <br/> |
   
### Return value

 **RGB**
  
## Remarks

The upper and lower limits of saturation are 0 and 240 respectively. There is no limit on the size of the integer you can pass for the  _int_ parameter, but saturation never exceeds these limits. 
  

