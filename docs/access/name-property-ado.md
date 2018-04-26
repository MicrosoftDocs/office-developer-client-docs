---
title: "Name Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4b19bd08-ac3c-86f0-471d-06a37a0d4f89

---

# Name Property (ADO)

Indicates the name of an object.
  
## Settings and Return Values

Sets or returns a **String** value that indicates the name of an object. 
  
## Remarks

Use the **Name** property to assign a name to or retrieve the name of a **Command**, **Property**, **Field**, or **Parameter** object. 
  
The value is read/write on a **Command** object and read-only on a **Property** object. 
  
For a **Field** object, **Name** is normally read-only. However, for new **Field** objects that have been appended to the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md), **Name** is read/write only after the [Value](value-property-ado.md) property for the **Field** has been specified and the data provider has successfully added the new **Field** by calling the [Update](update-method-ado.md) method of the **Fields** collection. 
  
For **Parameter** objects not yet appended to the [Parameters](parameters-collection-ado.md) collection, the **Name** property is read/write. For appended **Parameter** objects and all other objects, the **Name** property is read-only. Names do not have to be unique within a collection. 
  
You can retrieve the **Name** property of an object by an ordinal reference, after which you can refer to the object directly by name. For example, if  `rstMain.Properties(20).Name` yields  `Updatability`, you can subsequently refer to this property as yields  `Updatability`, you can subsequently refer to this property as  `rstMain.Properties("Updatability")`.
  

