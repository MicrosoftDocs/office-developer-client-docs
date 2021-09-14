---
title: "ANGLEALONGPATH Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: d7f8ca9a-3a89-abab-9805-bd1e24075c3f
description: "Returns the angle of the tangent to the path at a given point."
---

# ANGLEALONGPATH Function

Returns the angle of the tangent to the path at a given point.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

ANGLEALONGPATH(***section***, ***travel*** ***[,segment]*** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _section_ <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path).  <br/> |
| _travel_ <br/> |Required  <br/> |**Double** <br/> |The percentage along the path from begin point to end point. Must be between 0 and 1.  <br/> |
| _segment_ <br/> |Optional  <br/> |**Integer** <br/> |The 1-based segment of the path at which to calculate the tangent angle.  <br/> |
   
### Return value

 **Double**
  
## Remarks

If you include a  _segment_ value, ANGLEALONGPATH returns the value for that segment only. 
  
If you include a  _segment_ value, ANGLEALONGPATH determines the point of the tangent by using  _travel_ to calculate the percertage along  _segment_.
  
If either  _section_ or  _segment_ does not exist, Microsoft Visio returns #REF!. 
  

