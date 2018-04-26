---
title: "Field.DataUpdatable Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052988
  
localization_priority: Normal
ms.assetid: 08ca57b6-2d7c-36b4-7d51-b76ac5467163
description: "Returns a value that indicates whether the data in the field represented by a Field object is updatable."
---

# Field.DataUpdatable Property (DAO)

Returns a value that indicates whether the data in the field represented by a **[Field](field-object-dao.md)** object is updatable. 
  
## Syntax

 *expression*  . **DataUpdatable**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

Use this property to determine whether you can change the **[Value](field-value-property-dao.md)** property setting of a **Field** object. This property is always **False** on a **Field** object whose **[Attributes](field-attributes-property-dao.md)** property is **dbAutoIncrField**. 
  
You can use the **DataUpdatable** property on **Field** objects that are appended to the **[Fields](fields-collection-dao.md)** collection of **[QueryDef](querydef-object-dao.md)**, **[Recordset](recordset-object-dao.md)**, and **[Relation](relation-object-dao.md)** objects, but not the **Fields** collection of **[Index](index-object-dao.md)** or **[TableDef](tabledef-object-dao.md)** objects. 
  
## Example

This example demonstrates the **DataUpdatable** property using the first field from six different **Recordsets**. The DataOutput function is required for this procedure to run. 
  
```
Sub DataUpdatableX() 
 
 Dim dbsNorthwind As Database 
 Dim rstNorthwind As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 ' Open and print report about a table-type Recordset. 
 Set rstNorthwind = .OpenRecordset("Employees") 
 DataOutput rstNorthwind 
 
 ' Open and print report about a dynaset-type Recordset. 
 Set rstNorthwind = .OpenRecordset("Employees", _ 
 dbOpenDynaset) 
 DataOutput rstNorthwind 
 
 ' Open and print report about a snapshot-type Recordset. 
 Set rstNorthwind = .OpenRecordset("Employees", _ 
 dbOpenSnapshot) 
 DataOutput rstNorthwind 
 
 ' Open and print report about a forward-only-type Recordset. 
 Set rstNorthwind = .OpenRecordset("Employees", _ 
 dbOpenForwardOnly) 
 DataOutput rstNorthwind 
 
 ' Open and print report about a Recordset based on 
 ' a select query. 
 Set rstNorthwind = _ 
 .OpenRecordset("Current Product List") 
 DataOutput rstNorthwind 
 
 ' Open and print report about a Recordset based on a 
 ' select query that calculates totals. 
 Set rstNorthwind = .OpenRecordset("Order Subtotals") 
 DataOutput rstNorthwind 
 
 .Close 
 End With 
 
End Sub 
 
Function DataOutput(rstTemp As Recordset) 
 
 With rstTemp 
 Debug.Print "Recordset: " &amp; .Name &amp; ", "; 
 Select Case .Type 
 Case dbOpenTable 
 Debug.Print "dbOpenTable" 
 Case dbOpenDynaset 
 Debug.Print "dbOpenDynaset" 
 Case dbOpenSnapshot 
 Debug.Print "dbOpenSnapshot" 
 Case dbOpenForwardOnly 
 Debug.Print "dbOpenForwardOnly" 
 End Select 
 Debug.Print " Field: " &amp; .Fields(0).Name &amp; ", " &amp; _ 
 "DataUpdatable = " &amp; .Fields(0).DataUpdatable 
 Debug.Print 
 .Close 
 End With 
 
End Function 
 
```


