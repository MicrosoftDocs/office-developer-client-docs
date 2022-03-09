---
title: "GETREF Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251884
 
ms.localizationpriority: medium
ms.assetid: 25c9f817-d22b-28c9-1339-dc9f27d0dd41
description: "References a cell and doesn't recalculate the formula when the referenced cell changes."
---

# GETREF Function

References a cell and doesn't recalculate the formula when the referenced cell changes.
  
## Syntax

GETREF(***cellname*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *cellname* <br/> |Required  <br/> |**String** <br/> |The name of the cell to get a reference to. |

## Example

SETF(GETREF(PinX),5.1)
  
Sets the formula of the PinX cell to 5.1.
  