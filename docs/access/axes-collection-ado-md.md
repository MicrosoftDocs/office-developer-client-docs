---
title: "Axes Collection (ADO MD)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 7c719197-45f1-a5b9-665d-25cb693b1eb0
---

# Axes Collection (ADO MD)

Contains the [Axis](axis-object-ado-md.md) objects that define a cellset. 
  
## Remarks

A [Cellset](cellset-object-ado-md.md) object contains an **Axes** collection. Once the **Cellset** is opened, this collection will contain at least one **Axis**. See the [Axis](axis-object-ado-md.md) object for a more detailed explanation of how to use **Axis** objects. 
  
> [!NOTE]
> The filter axis of a **Cellset** is not contained in the **Axes** collection. See the [FilterAxis](filteraxis-property-ado-md.md) property for more information. 
  
 **Axes** is a standard ADO collection. With the properties and methods of a collection, you can do the following: 
  
- Obtain the number of objects in the collection with the [Count](count-property-ado.md) property. 
    
- Return an object from the collection with the default [Item](item-property-ado.md) property. 
    
- Update the objects in the collection from the provider with the [Refresh](refresh-method-ado.md) method. 
    

