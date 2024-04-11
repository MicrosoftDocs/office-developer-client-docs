---
title: "LISTSHEETREF Function"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 87ddbc35-8577-0a96-20b8-aa7734764c5b
description: "Returns a sheet reference to the list container shape that contains the shape."
---

# LISTSHEETREF Function

Returns a sheet reference to the list container shape that contains the shape.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

LISTMEMBERCOUNT()
  
### Return value

ShapeSheet reference
  
## Remarks

If the shape is not a list member, the LISTSHEETREF function returns #REF!.
  
## Example

LISTSHEETREF(1)!Height 
  
Returns the value in the Height cell of the list container shape that contains the shape. 
  

