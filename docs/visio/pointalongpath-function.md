---
title: "POINTALONGPATH Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 7f91e5d9-89b8-5a0d-e01f-aa81fbd5e1fd
description: "Returns the coordinates of a point on, or offset from, the path."
---

# POINTALONGPATH Function

Returns the coordinates of a point on, or offset from, the path.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

POINTALONGPATH( ** *section* **, ** *travel* ** ** *[,offset]* ** ** *[,segment]* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _section_ <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path).  <br/> |
| _travel_ <br/> |Required  <br/> |**Double** <br/> |The percentage of the path traversed, from the begin point to the end point that identifies the point. Must be between 0 and 1.  <br/> |
| _offset_ <br/> |Optional  <br/> |**Double** <br/> |The distance that the point is offset from the path. See Remarks for more information.  <br/> |
| _segment_ <br/> |Optional  <br/> |**Integer** <br/> |The 1-based segment of the path in which to calculate the coordinates.  <br/> |
   
### Return Value

 **Point**
  
## Remarks

If  _section_ or  _segment_ does not exist, Microsoft Visio returns #REF!. 
  
Positive  *offset*  values specify points to the left of the direction of travel. 
  
Negative  *offset*  values specify points to the right of the direction of travel. 
  
A **Point** represents an ordered pair of geometric coordinates (  *x,y*  ) as a single value. 
  

