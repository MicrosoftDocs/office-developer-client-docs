---
title: "CALLOUTTARGETREF Function"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: c67cfd32-5911-d8e9-dd51-fd4885dd2b0d
description: "Returns a sheet reference to the target shape of the callout shape."
---

# CALLOUTTARGETREF Function

Returns a sheet reference to the target shape of the callout shape.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

CALLOUTTARGETREF()!
  
### Return value

ShapeSheet reference
  
## Remarks

If the shape is not a callout shape, or if it is not associated with a target shape, CALLOUTTARGETREF returns #REF.
  
## Example

CALLOUTTARGETREF()!Height 
  
Returns the value in the Height cell of the shape that is associated with the callout. 
  

