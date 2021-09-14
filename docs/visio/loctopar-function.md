---
title: "LOCTOPAR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251585
 
ms.localizationpriority: medium
ms.assetid: ce1028d6-0293-e8dd-b79d-3f02c50f6250
description: "Returns a transformed point in parent coordinates in the destination coordinate system."
---

# LOCTOPAR Function

Returns a transformed point in parent coordinates in the destination coordinate system.
  
## Syntax

LOCTOPAR(** *srcPoint* **, ** *srcRef* **, ** *dstRef* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _srcPoint_ <br/> |Required  <br/> |**String** <br/> | A point in local coordinates in the source coordinate system.  <br/> |
| _srcRef_ <br/> |Required  <br/> |**String** <br/> | A reference to a cell in the source object.  <br/> |
| _dstRef_ <br/> |Required  <br/> |**String** <br/> | A reference to a cell in the destination object.  <br/> |
   
### Return value

String
  
## Remarks

Converts a point from local coordinates in a source shape to parent coordinates in a destination shape. You can use the LOCTOPAR function to set parent coordinates in cells, such as PinX, PinY, BeginX, and BeginY in a shape using another point from another coordinate system. 
  
This function works even when the source and destination shapes are within groups. It also adjusts for rotation and flips in the intermediate transformation. 
  
The source and destination coordinates must be on the same page. 
  
If the destination is a page, which has no parent, the result is expressed in the page's local coordinates. 
  
## Example

LOCTOPAR(PNT(LocPinX, LocPinY), Width, Sheet.4!Width) 
  
Converts the local pin of the shape associated with the formula to parent coordinates of Sheet.4. 
  

