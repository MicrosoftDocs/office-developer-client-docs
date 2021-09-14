---
title: "TINT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: c4f176d6-4af0-282d-5640-7d98e84dfb55
description: "Modifies the color by increasing its luminosity by the amount (positive or negative) specified in the int parameter."
---

# TINT Function

Modifies the color by increasing its luminosity by the amount (positive or negative) specified in the  _int_ parameter. 
  
## Syntax

TINT(** *color* **, ** *int* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _color_ <br/> |Required  <br/> |**Numeric** <br/> |The Microsoft Visio color index or RGB value of the color.  <br/> |
| _int_ <br/> |Required  <br/> |**Integer** <br/> |The amount by which to increase the luminosity of the color. Can be positive or negative.  <br/> |
   
### Return value

 **RGB**
  
## Remarks

The upper and lower limits of luminosity are 0 and 240 respectively. There is no limit on the size of the integer you can pass for the  _int_ parameter, but luminosity never exceeds these limits. 
  

