---
title: "Property.Inherited Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052991
  
localization_priority: Normal
ms.assetid: 10e624db-2301-b9be-beca-6e8caccf7274
description: "Returns a value that indicates whether a Property object is inherited from an underlying object."
---

# Property.Inherited Property (DAO)

Returns a value that indicates whether a **[Property](property-object-dao.md)** object is inherited from an underlying object. 
  
## Syntax

 *expression*  . **Inherited**
  
 *expression*  A variable that represents a **Property** object. 
  
## Remarks

For built-in **Property** objects that represent predefined properties, the only possible return value is **False**. 
  
You can use the **Inherited** property to determine whether a user-defined **Property** was created for the object it applies to, or whether the **Property** was inherited from another object. For example, suppose you create a new **Property** for a **[QueryDef](querydef-object-dao.md)** object and then open a **[Recordset](recordset-object-dao.md)** object from the **QueryDef** object. This new **Property** will be part of the **Recordset** object's **[Properties](properties-collection-dao.md)** collection, and its **Inherited** property will be set to **True** because the property was created for the **QueryDef** object, not the **Recordset** object. 
  
## Example

This example use the **Inherited** property to determine if a user-defined **Property** object was created for a **Recordset** object or for some underlying object. 
  
```
Sub InheritedX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfTest As TableDef 
 Dim rstTest As Recordset 
 Dim prpNew As Property 
 Dim prpLoop As Property 
 
 ' Create a new property for a saved TableDef object, then 
 ' open a recordset from that TableDef object. 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfTest = dbsNorthwind.TableDefs(0) 
 Set prpNew = tdfTest.CreateProperty("NewProperty", _ 
 dbBoolean, True) 
 tdfTest.Properties.Append prpNew 
 Set rstTest = tdfTest.OpenRecordset(dbOpenForwardOnly) 
 
 ' Show Name and Inherited property of the new Property 
 ' object in the TableDef. 
 Debug.Print "NewProperty of " &amp; tdfTest.Name &amp; _ 
 " TableDef:" 
 Debug.Print " Inherited = " &amp; _ 
 tdfTest.Properties("NewProperty").Inherited 
 
 ' Show Name and Inherited property of the new Property 
 ' object in the Recordset. 
 Debug.Print "NewProperty of " &amp; rstTest.Name &amp; _ 
 " Recordset:" 
 Debug.Print " Inherited = " &amp; _ 
 rstTest.Properties("NewProperty").Inherited 
 
 ' Delete new TableDef because this is a demonstration. 
 tdfTest.Properties.Delete prpNew.Name 
 dbsNorthwind.Close 
 
End Sub 
 
```


