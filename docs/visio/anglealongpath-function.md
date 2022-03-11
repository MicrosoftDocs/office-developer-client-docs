---
title: "ANGLEALONGPATH Function" 
manager: lindalu
ms.date: 03/09/2022
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
| *section* <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path). |
| *travel* <br/> |Required  <br/> |**Double** <br/> |The percentage along the path from begin point to end point. Must be between 0 and 1. |
| *segment* <br/> |Optional  <br/> |**Integer** <br/> |The 1-based segment of the path at which to calculate the tangent angle. |

### Return value

 **Double**
  
## Remarks

If you include a *segment* value, ANGLEALONGPATH returns the value for that segment only.
  
If you include a *segment* value, ANGLEALONGPATH determines the point of the tangent by using *travel* to calculate the percertage along *segment*.
  
If either *section* or  segment_ does not exist, Microsoft Visio returns #REF!.
  