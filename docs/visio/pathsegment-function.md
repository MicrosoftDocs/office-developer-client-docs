---
title: "PATHSEGMENT Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 08accf3b-93ac-9dd3-85ce-34ad42e79a4f
description: "Returns the 1-based segment number at the specified percentage mark along the specified path."
---

# PATHSEGMENT Function

Returns the 1-based segment number at the specified percentage mark along the specified path.
  
## Syntax

PATHSEGMENT( ** *section* **, ** *travel* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _section_ <br/> |Required  <br/> |**String** <br/> |The Geometry section that represents the path, specified by a reference to its Path cell (for example, Geometry1.Path).  <br/> |
| _travel_ <br/> |Required  <br/> |**Double** <br/> |The percentage of the path traversed, from the begin point to the end point. Must be between 0 and 1.  <br/> |
   
### Return value

Integer
  

