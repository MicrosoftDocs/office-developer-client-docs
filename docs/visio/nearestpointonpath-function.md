---
title: "NEARESTPOINTONPATH Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 539bf79a-df09-2048-2aba-8c863dd26fc2
description: "Returns the percentage of the distance along the path of the point that is nearest to the specified coordinates, as a value between 0 and 1."
---

# NEARESTPOINTONPATH Function

Returns the percentage of the distance along the path of the point that is nearest to the specified coordinates, as a value between 0 and 1.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

NEARESTPOINTONPATH( ** *section* **, ** *x* **, ** *y* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _section_ <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path).  <br/> |
| _x_ <br/> |Required  <br/> |**Double** <br/> |The  _x_-coordinate of the specified point.  <br/> |
| _y_ <br/> |Required  <br/> |**Double** <br/> |The  _y_-coordinate of the specified point.  <br/> |
   
### Return Value

 **Double**
  
## Remarks

If  _section_ does not exist, Microsoft Visio returns #REF!. 
  

