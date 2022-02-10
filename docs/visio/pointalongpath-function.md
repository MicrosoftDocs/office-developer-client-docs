---
title: "POINTALONGPATH Function" 
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: reference 
ms.localizationpriority: medium
ms.assetid: 7f91e5d9-89b8-5a0d-e01f-aa81fbd5e1fd
description: "Returns the coordinates of a point on, or offset from, the path."
---

# POINTALONGPATH Function

Returns the coordinates of a point on, or offset from, the path.
  
## Version Information

Version Added: Visio 2010
  
## Syntax

POINTALONGPATH(***section***, ***travel*** ***[,offset]*** ***[,segment]*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *section* |Required |**String** |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path). |
| *travel* |Required |**Double** |The percentage of the path traversed, from the begin point to the end point that identifies the point. Must be between 0 and 1. |
| *offset* |Optional |**Double** |The distance that the point is offset from the path. See Remarks for more information. |
| *segment* |Optional |**Integer** |The 1-based segment of the path in which to calculate the coordinates. |

### Return value

**Point**
  
## Remarks

If *section* or *segment* does not exist, Microsoft Visio returns #REF!.
  
Positive  *offset*  values specify points to the left of the direction of travel.
  
Negative  *offset*  values specify points to the right of the direction of travel.
  
A **Point** represents an ordered pair of geometric coordinates (*x,y*) as a single value.
