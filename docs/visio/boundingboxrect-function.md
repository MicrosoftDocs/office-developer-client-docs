---
title: "BOUNDINGBOXRECT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 1f66d2b2-ec9e-cd58-7642-96850fe4589e
description: "Returns the coordinate of the specified edge of the shape's bounding box."
---

# BOUNDINGBOXRECT Function

Returns the coordinate of the specified edge of the shape's bounding box.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

BOUNDINGBOXRECT(** *Index* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Index_ <br/> |Required  <br/> |**Integer** <br/> |The edge of the shape's bounding box for which to get the coordinate. See Remarks for possible values. |
   
### Return value

 **Number**
  
## Remarks

 *Index*  can be one of the following values. 
  
|**Item**|**Value**|
|:-----|:-----|
|Left edge  <br/> |0  <br/> |
|Right edge  <br/> |1  <br/> |
|Top edge  <br/> |2  <br/> |
|Bottom edge  <br/> |3  <br/> |
   
If the shape has a parent, the return value is in the coordinate system of that parent.
  

