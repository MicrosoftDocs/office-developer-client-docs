---
title: "GETVAL Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251885
 
ms.localizationpriority: medium
ms.assetid: 1da42991-5791-ebab-84cc-286cfe984a61
description: "Gets the value of a cell and doesn't recalculate the formula when the cell's value changes."
---

# GETVAL Function

Gets the value of a cell and doesn't recalculate the formula when the cell's value changes.
  
## Syntax

GETVAL(** *cellname* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellname_ <br/> |Required  <br/> |**String** <br/> |The name of the cell to get the value of. |
   
## Example

GETVAL(PinX) + GETVAL(PinY) + Width 
  
Returns the sum of the value of the PinX, PinY, and Width cells. 
  

