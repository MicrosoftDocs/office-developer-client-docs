---
title: "LOC Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251455
 
ms.localizationpriority: medium
ms.assetid: 7db7a8ed-50a9-8495-b978-42a2fddb466a
description: "Takes a point defined in one shape's local coordinates and returns the equivalent point expressed in the local coordinates of the shape associated with the formula."
---

# LOC Function (VisioShapeSheet)

Takes a point defined in one shape's local coordinates and returns the equivalent point expressed in the local coordinates of the shape associated with the formula.
  
## Syntax

LOC(***point*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *point* <br/> |Required  <br/> |**String** <br/> | A point defined in one shape's local coordinates. |

### Return value

String
  
## Remarks

Local coordinates are measured from the lower-left corner of the shape's selection rectangle. Both shapes must be on the same page.
  
## Example

LOC(PNT(Sheet.5!LocPinX, Sheet.5!LocPinY))
  
In this expression, PNT converts a set of local coordinates in Sheet.5 to a point. (Sheet.5 is another shape on the same drawing page.) LOC then converts that point to an equivalent point in the current shape's local coordinate system, relative to the lower-left corner of the selection rectangle of the current shape.
  
The 5 in Sheet.5 is the ID number for the shape, which is displayed in the **Shape Name** dialog box (**Developer** tab).
  