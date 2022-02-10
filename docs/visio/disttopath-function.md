---
title: "DISTTOPATH Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 2ba7d372-0c2a-9fa7-0af6-97da0aafdb12
description: "Returns the shortest distance from the point represented by the specified coordinates to a point on the path."
---

# DISTTOPATH Function

Returns the shortest distance from the point represented by the specified coordinates to a point on the path.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

DISTTOPATH(***section***, ***x***, ***y*** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _section_ <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path). |
| _x_ <br/> |Required  <br/> |**Double** <br/> |The  _x_-coordinate of the point. |
| _y_ <br/> |Required  <br/> |**Double** <br/> |The  _y_-coordinate of the point. |
   
### Return value

 **Double**
  
## Remarks

Microsoft Visio returns #REF! if  _section_ does not exist. 
  
The returned value is positive if the point is to the left of the direction of travel; it is negative if the point is to the right of the direction of travel.
  

