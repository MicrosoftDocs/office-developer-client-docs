---
title: "Recordsets Collection (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 246d9a78-4ce8-6393-982b-77ac00cd85bb
description: "A Recordsets collection contains all open Recordset objects in a Connection or Database object."
---

# Recordsets Collection (DAO)

A **Recordsets** collection contains all open **Recordset** objects in a **Connection** or **Database** object. 
  
## Remarks

When you use DAO objects, you manipulate data almost entirely using **Recordset** objects. 
  
A new **Recordset** object is automatically added to the **Recordsets** collection when you open the **Recordset** object, and is automatically removed when you close it. 
  
You can create as many **Recordset** object variables as needed. Different **Recordset** objects can access the same tables, queries, and fields without conflicting. 
  
To refer to a **Recordset** object in a collection by its ordinal number or by its **Name** property setting, use any of the following syntax forms: 
  
 **Recordsets** (0) 
  
 **Recordsets** ("  _name_")
  
 **Recordsets** ![  _name_]
  
> [!NOTE]
> You can open a **Recordset** object from the same data source or database more than once, creating duplicate names in the **Recordsets** collection. You should assign **Recordset** objects to object variables and refer to them by variable name. 
  
## Example

This example demonstrates **Recordset** objects and the **Recordsets** collection by opening four different types of **Recordsets**, enumerating the Recordsets collection of the current **Database**, and enumerating the **Properties** collection of each **Recordset**. 
  
```
Sub RecordsetX() 
 
 Dim dbsNorthwind As Database 
 Dim rstTable As Recordset 
 Dim rstDynaset As Recordset 
 Dim rstSnapshot As Recordset 
 Dim rstForwardOnly As Recordset 
 Dim rstLoop As Recordset 
 Dim prpLoop As Property 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 
 ' Open one of each type of Recordset object. 
 Set rstTable = .OpenRecordset("Categories", _ 
 dbOpenTable) 
 Set rstDynaset = .OpenRecordset("Employees", _ 
 dbOpenDynaset) 
 Set rstSnapshot = .OpenRecordset("Shippers", _ 
 dbOpenSnapshot) 
 Set rstForwardOnly = .OpenRecordset _ 
 ("Employees", dbOpenForwardOnly) 
 
 Debug.Print "Recordsets in Recordsets " &amp; _ 
 "collection of dbsNorthwind" 
 
 ' Enumerate Recordsets collection. 
 For Each rstLoop In .Recordsets 
 
 With rstLoop 
 Debug.Print " " &amp; .Name 
 
 ' Enumerate Properties collection of each 
 ' Recordset object. Trap for any 
 ' properties whose values are invalid in 
 ' this context. 
 For Each prpLoop In .Properties 
 On Error Resume Next 
 If prpLoop <> "" Then Debug.Print _ 
 " " &amp; prpLoop.Name &amp; _ 
 " = " &amp; prpLoop 
 On Error GoTo 0 
 Next prpLoop 
 
 End With 
 
 Next rstLoop 
 
 rstTable.Close 
 rstDynaset.Close 
 rstSnapshot.Close 
 rstForwardOnly.Close 
 
 .Close 
 End With 
 
End Sub 

```


