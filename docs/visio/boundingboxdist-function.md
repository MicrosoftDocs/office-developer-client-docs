---
title: "BOUNDINGBOXDIST Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 8a2490f2-48c4-5df3-a3b3-40e8e0c80479
description: "Returns the measurement of the specified part of the shape's bounding box."
---

# BOUNDINGBOXDIST Function

Returns the measurement of the specified part of the shape's bounding box. 
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

BOUNDINGBOXDIST(** *Index* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Index_ <br/> |Required  <br/> |**Number** <br/> |The part of the shape's bounding box to measure and return. See Remarks for possible values.  <br/> |
   
### Return value

 **Number**
  
## Remarks

 *Index*  can be one of the following values. 
  
|**Item**|**Value**|
|:-----|:-----|
|Width  <br/> |0  <br/> |
|Height  <br/> |1  <br/> |
|Left edge to shape pin  <br/> |2  <br/> |
|Shape pin to right edge  <br/> |3  <br/> |
|Shape pin to top edge  <br/> |4  <br/> |
|Bottom edge to shape pin  <br/> |5  <br/> |
|Center of bounding box to PinX  <br/> |6  <br/> |
|Center of bounding box to PinY  <br/> |7  <br/> |
   

