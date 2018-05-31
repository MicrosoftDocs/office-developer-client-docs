---
title: "SETATREFEXPR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1027317
 
localization_priority: Normal
ms.assetid: c1bd7819-b53b-bff1-69c1-6d78e8fb278b
description: "Stores a value that is set through an action in the user interface (UI) or Automation."
---

# SETATREFEXPR Function

Stores a value that is set through an action in the user interface (UI) or Automation.
  
## Syntax

SETATREFEXPR ([ ** *expr_opt* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expr_opt_ <br/> |Optional  <br/> |**Varies** <br/> |An expression that is replaced by the value or expression being assigned to the referenced cell in the SETATREF function. If not indicated, its initial value is 0 (zero).  <br/> |
   
## Remarks

The value of a SETATREFEXPR expression can also be set from a SETATREF function in another cell that references the cell containing the SETATREFEXPR expression. 
  
You are not limited to using the SETATREFEXPR function as a parameter to the SETATREF function. 
  
## Example 1

The following example uses the SETATREFEXPR function to ensure that a shape is as wide as its text.
  
Width =MAX(TEXTWIDTH(TheText),SETATREFEXPR())
  
## Example 2

The following example shows how you can use the SETATREFEXPR function to cause your shapes to snap to a custom grid. The SETATREFEXPR formulas are placed in the PinX and PinY cells, causing the shape's pin to snap to the grid defined in User.GridX and User.GridY. 
  
User.GridX =2 in
  
User.GridY =2 in
  
PinX =INT(SETATREFEXPR()/User.GridX + .5)\*User.GridX
  
PinY =INT(SETATREFEXPR()/User.GridY + .5)\*User.GridY
  
## Example 3

For an example using the SETATREFEXPR function with the SETATREF function, see the [SETATREF](setatref-function.md) function. 
  

