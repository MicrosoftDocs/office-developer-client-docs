---
title: "CONTAINERSHEETREF Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: bbdb2dea-4f75-b73e-a98a-0031f34dff2c
description: "Returns a sheet reference to the specified container that contains the shape."
---

# CONTAINERSHEETREF Function

Returns a sheet reference to the specified container that contains the shape.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

CONTAINERSHEETREF(** *index* ** ** *[, category]* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _index_ <br/> |Required  <br/> |**Integer** <br/> |The 1-based index of the container. See Remarks for more information. |
| _category_ <br/> |Optional  <br/> |**String** <br/> |The category of the container. See Remarks for more information. |
   
### Return value

ShapeSheet reference
  
## Remarks

The index of a container is calculated based on the z-order of containers from front to back.
  
 *Categories*  are user-defined strings that you can use to categorize shapes. You can define categories in the User.msvShapeCategories cell in the ShapeSheet for a shape. You can define multiple categories for a shape by separating the categories with semi-colons. 
  
If the shape is not a member of a container, or if there is no container that matches both the specified index number and the category, CONTAINERSHEETREF returns #REF!.
  
## Example

CONTAINERSHEETREF(1)!Height 
  
Returns the value in the Height cell of the container that is most forward on the page to which the shape belongs. 
  

