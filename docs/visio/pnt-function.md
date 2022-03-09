---
title: "PNT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251480
 
ms.localizationpriority: medium
ms.assetid: d14a735c-0278-922f-7823-79adf6cb1e64
description: "Returns the point represented by the coordinates x and y as a single value."
---

# PNT Function

Returns the point represented by the coordinates _x_ and _y_ as a single value.
  
## Syntax

PNT(***x,y*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _x,y_ <br/> |Required  <br/> |**Number, Number** <br/> |The coordinates of the point in the coordinate system of the current shape. |

### Return value

Point
  
## Remarks

Converting coordinates to points allows you to change a shape's geometry without having to manipulate _x_ - and _y_ -coordinates separately.
  
## Example

PNT(PinX,PinY)
  
Returns the point represented by PinX and PinY.
  