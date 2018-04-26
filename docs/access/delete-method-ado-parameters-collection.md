---
title: "Delete Method (ADO Parameters Collection)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 03ffc24d-fea2-30fa-c8e9-43eb524fd51f
---

# Delete Method (ADO Parameters Collection)

Deletes an object from the [Parameters](parameters-collection-ado.md) collection. 
  
## Syntax

 *Parameters*  . **Delete** * Index * 
  
## Parameters

-  *Index* 
    
- A **String** value that contains the name of the object you want to delete, or the objects ordinal position (index) in the collection. 
    
## Remarks

Using the **Delete** method on a collection lets you remove one of the objects in the collection. This method is available only on the **Parameters** collection of a [Command](command-object-ado.md) object. You must use the [Parameter](parameter-object-ado.md) object's [Name](name-property-ado.md) property or its collection index when calling the **Delete** method — an object variable is not a valid argument. 
  

