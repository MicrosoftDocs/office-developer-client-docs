---
title: "DEPENDSON Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251420
 
localization_priority: Normal
ms.assetid: 8fcfcfdd-69e2-b061-fdb6-d29389d14403
description: "Creates a cell reference dependency."
---

# DEPENDSON Function

Creates a cell reference dependency.
  
## Syntax

DEPENDSON(** *cellref* ** [, ** *cellref2* **,...]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellref_ <br/> |Required  <br/> |**String** <br/> |The first cell reference.  <br/> |
| _cellref2_ <br/> |Optional  <br/> |**String** <br/> |The second cell reference.  <br/> |
   
## Remarks

This function always returns FALSE. It has no effect when used in an Event row or an Action cell. 
  
## Example

OPENTEXTWIN() + DEPENDSON(PinX,PinY) 
  
Opens the text block for a shape whenever the shape's PinX or PinY cells change. 
  

