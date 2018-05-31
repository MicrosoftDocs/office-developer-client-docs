---
title: "SETATREF Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60113
 
localization_priority: Normal
ms.assetid: 1ecfdb05-2533-470a-006b-e554026944d8
description: "Redirects updated values resulting from actions in the user interface (UI) or Automation to another cell."
---

# SETATREF Function

Redirects updated values resulting from actions in the user interface (UI) or Automation to another cell. 
  
## Syntax

SETATREF(** *reference* ** [, ** *set_expression* ** [, ** *ignore_eval* ** ]]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _reference_ <br/> |Required  <br/> |**String** <br/> |A reference to the cell where updates are redirected.  <br/> |
| _set_expression_ <br/> |Optional  <br/> |**String** <br/> |An expression that is assigned to  _reference_.  <br/> |
| _ignore_eval_ <br/> |Optional  <br/> |**Boolean** <br/> |If TRUE, the SETATREF function evaluates to (0) zero; if FALSE (the default) the SETATREF function evaluates to the value of  _reference_.  <br/> |
   
## Remarks

When a user action in the drawing window, or an Automation method, causes Microsoft Visio to update a cell containing a SETATREF formula, the value is instead redirected to the cell referenced by the SETATREF formula ( _reference_). The formula in the cell containing the SETATREF function remains intact.
  
If  _set_expression_ is omitted, the value set in the UI or by using Automation is assigned to the referenced cell; otherwise, the contents of  _set_expression_ are assigned to the referenced cell. This allows the new value to be modified or transformed before being assigned to the referenced cell. 
  
The SETATREF function has two related functions: 
  
- The SETATREFEXPR function, which you can use to represent the new value within  _set_expression_. For example, a  _set_expression_ of SETATREFEXPR()-2 in. could be used to subtract 2 inches from the SETATREFEXPR result. 
    
- The SETATREFEVAL function, which you can use to indicate that some portion of  _set_expression_ should be evaluated and replaced by its result. 
    
The SETATREF function is designed for use in cells that can be changed by user actions in the drawing window. The following cells are supported:
  
- ShapeTransform section—Width, Height, Angle, PinX, and PinY cells
    
- Text Transform section—TxtWidth, TxtHeight, TxtAngle, TxtPinX, and TxtPinY cells
    
- 1-D Endpoints section—BeginX, BeginY, EndX, and EndY cells
    
- Controls section—Controls.X and Controls.Y cells
    
- Shape Data section
    
Because SETATREF changes the location where cell values change, it affects event firing. If a cell contains SETATREF, the **FormulaChanged** and **CellChanged** events fire for the cell that is referenced by SETATREF, not the cell containing SETATREF. If a cell containing SETATREF also contains SETATREFEXPR, the **FormulaChanged** event also fires for the cell containing SETATREF because a function parameter is changed. 
  
Other important points to note about the SETATREF function include the following:
  
- SETATREF functions can chain up to 10 references to other SETATREF functions. 
    
- Cells can contain other expressions in addition to the SETATREF function, including multiple occurrences of SETATREF in a single cell.
    
- If shapes are glued, Visio follows the SETATREF reference chain within the same sheet and places glue formulas in the referenced cell. 
    
- Automation recognizes the SETATREF function and follows the chain of referenced cells. 
    
- Like GUARD, SETATREF does not protect cells from changes made by using the SETF function in the ShapeSheet.
    
## Example1

Let's say that a shape has a custom property called Width, and that the Width cell in the Shape Transform section contains the following formula:
  
=SETATREF(Prop.Width)
  
If a user were to change the shape's width in the UI, the new value is assigned to the Prop.Width cell, not to the Width cell in the ShapeTransform section; the formula in the Width cell remains unchanged. You can also set the shape's width by using shape data.
  
## Example2

Visio solutions often have shapes that have a hierarchical relationship, requiring child shapes to move when a parent shape is moved. Following is an example of how you might manage this relationship using the SETATREF function in the ShapeSheet. 
  
The following formulas are contained in the Shape Transform section of the child shape. Also, we define user cells called User.DeltaX and User.DeltaY, which track the offset dimension from ParentShape. This allows the child shape to move when the parent shape is moved, and also to preserve the hierarchical relationship if the child shape is moved.
  
PinX =SETATREF(User.DeltaX, SETATREFEVAL(SETATREFEXPR() - ParentShape!PinX)) + ParentShape!PinX
  
PinY =SETATREF(User.DeltaY, SETATREFEVAL(SETATREFEXPR() - ParentShape!PinY)) + ParentShape!PinY
  
When the child shape is moved using the UI, the new PinX and PinY values are set as the parameter in the SETATREFEXPR function. The SETATREF function evaluates the formula enclosed in SETATREFEVAL and replaces PinX and PinY with their results, and then the resulting formula is assigned to the user cells referenced in the SETATREF function—User.DeltaX and User.DeltaY. Lastly, the values returned by SETATREF (User.DeltaX or User.DeltaY) are added to the pin location of ParentShape to calculate the child shape's pin location.
  

