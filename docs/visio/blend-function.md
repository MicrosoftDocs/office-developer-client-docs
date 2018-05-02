---
title: "BLEND Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: c67b46bb-0eb2-f094-2870-c320bd488705
description: "Blends two colors in the proportion specified by the float parameter."
---

# BLEND Function

Blends two colors in the proportion specified by the  _float_ parameter. 
  
## Syntax

BLEND( ** *color1* **, ** *color2* **, ** *float[0,1]* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _color1_ <br/> |Required  <br/> |**Numeric** <br/> |The Visio color index or RGB value of the first color.  <br/> |
| _color2_ <br/> |Required  <br/> |**Numeric** <br/> |The Visio color index or RGB value of the second color.  <br/> |
| _float[0,1]_ <br/> |Required  <br/> |**Float** <br/> |The proportion in which to blend  _color2_ and  _color1_, respectively. A real number from 0 to 1 inclusive.  <br/> |
   
### Return Value

 **RGB**
  
## Remarks

The color returned is determined by the relative proportions in which to blend  _color2_ and  _color1_, respectively, as specified by the  _float_ parameter. For example, if  _float_ is 0.25, the color returned is composed 75% of  _color1_ and 25% of  _color2_. 
  
Another way to think about it is that the  _float_ value corresponds to the point along the color spectrum from  _color1_ to  _color2_. Therefore, smaller numbers (closer to zero) for  _float_ produce blends closer to  _color1_, while larger numbers (closer to 1) produce blends closer to  _color2_.
  

