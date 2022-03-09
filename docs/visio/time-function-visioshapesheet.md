---
title: "TIME Function (VisioShapeSheet)" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251506
 
ms.localizationpriority: medium
ms.assetid: 2e662230-0760-5f43-52dc-927f499715f6
description: "Returns the time represented by hour, minute, and second."
---

# TIME Function (VisioShapeSheet)

Returns the time represented by _hour_, _minute_, and _second_.
  
## Syntax

TIME(***hour***, ***minute***, ***second***)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _hour_ <br/> |Required  <br/> |**Numeric** <br/> |The hour component. |
| _minute_ <br/> |Required  <br/> |**Numeric** <br/> |The minute comonent. |
| _second_ <br/> |Required  <br/> |**Numeric** <br/> |The second component. |

### Return value

Numeric
  
## Example 1

TIME(15,30,30)
  
Returns the value representing 15:30:30.
  
## Example 2

FORMAT(TIME(15,30,30),"HH:mm")
  
Returns the value representing 15:30.
  
## Example 3

TIME(15,30,30) + 8 eh.
  
Returns the value representing 23:30:30.
  