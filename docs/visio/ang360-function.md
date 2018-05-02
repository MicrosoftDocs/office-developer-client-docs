---
title: "ANG360 Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251392
 
localization_priority: Normal
ms.assetid: 23e6899d-0a94-a7d8-8de2-091e0531f163
description: "Normalizes an angle's range to be 0 \<= result \< 2PI radians (0 \<= result \< 360 degrees)."
---

# ANG360 Function

Normalizes an angle's range to be 0 \<= result \< 2PI radians (0 \<= result \< 360 degrees).
  
## Syntax

ANG360( ** *angle* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _angle_ <br/> |Required  <br/> |**Numeric** <br/> |The angle to be normalized.  <br/> |
   
## Remarks

If  *angle*  is not specified by using angular units, it is interpreted as radians. If  *angle*  cannot be converted to a value, a #VALUE! error is returned. 
  
## Example 1

ANG360(395 deg)
  
Returns 35 deg
  
## Example 2

ANG360(-9.8 rad)
  
Returns 2.7664 rad
  
## Example 3

ANG360(45)
  
Returns 58.31 deg (1.0177 rad)
  

