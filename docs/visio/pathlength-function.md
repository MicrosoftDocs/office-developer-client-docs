---
title: "PATHLENGTH Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6f47ea08-fb5e-7d48-e84a-2a6570564924
description: "Returns the length of the path that is defined in the specified Geometry section."
---

# PATHLENGTH Function

Returns the length of the path that is defined in the specified Geometry section.
  
## Version Information

Version Added: Visio 2010
  
## Syntax

PATHLENGTH(***section*** ***[,segment]*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *section* <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path). |
| *segment* <br/> |Optional  <br/> |**Integer** <br/> |The 1-based segment of the path to measure. |

### Return value

 **Double**
  
## Remarks

If *section* or *segment* does not exist, Microsoft Visio returns #REF!.
  
If you include a *segment* value, PATHLENGTH returns the length of that segment only.
