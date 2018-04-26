---
title: "Item Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 793c305f-0e5b-a529-e21f-b7ab0843ed49

---

# Item Property (ADO)

Indicates a specific member of a collection, by name or ordinal number.
  
## Syntax

 **Set** *object*  =  *collection*  . **Item** ( Index ) 
  
## Return Value

Returns an object reference.
  
## Parameters

-  *Index* 
    
- A **Variant** expression that evaluates either to the name or to the ordinal number of an object in a collection. 
    
## Remarks

Use the **Item** property to return a specific object in a collection. If **Item** cannot find an object in the collection corresponding to the  *Index*  argument, an error occurs. Also, some collections don't support named objects; for these collections, you must use ordinal number references. 
  
The **Item** property is the default property for all collections; therefore, the following syntax forms are interchangeable: 
  
```
collection.Item (Index)
collection (Index)

```


