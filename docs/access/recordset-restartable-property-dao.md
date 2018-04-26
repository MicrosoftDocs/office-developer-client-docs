---
title: "Recordset.Restartable Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052926
  
localization_priority: Normal
ms.assetid: 00def49d-ea7e-6cd5-2f4a-914a1ddcdd51
description: "Returns a value that indicates whether a Recordset object supports the Requery method, which re-executes the query on which the Recordset object is based."
---

# Recordset.Restartable Property (DAO)

Returns a value that indicates whether a **[Recordset](recordset-object-dao.md)** object supports the **[Requery](recordset-requery-method-dao.md)** method, which re-executes the query on which the **Recordset** object is based. 
  
## Syntax

 *expression*  . **Restartable**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

Table-type **Recordset** objects always return **False**. 
  
Check the **Restartable** property before using the **Requery** method on a **Recordset** object. If the object's **Restartable** property is set to **False**, use the **[OpenRecordset](connection-openrecordset-method-dao.md)** method on the underlying **[QueryDef](querydef-object-dao.md)** object to re-execute the query. 
  
## Example

This example demonstrates the **Restartable** property with different **Recordset** objects. 
  
```
Sub RestartableX() 
 
 Dim dbsNorthwind As Database 
 Dim rstTemp As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 ' Open a table-type Recordset and print its 
 ' Restartable property. 
 Set rstTemp = .OpenRecordset("Employees", dbOpenTable) 
 Debug.Print _ 
 "Table-type recordset from Employees table" 
 Debug.Print " Restartable = " &amp; rstTemp.Restartable 
 rstTemp.Close 
 
 ' Open a Recordset from an SQL statement and print its 
 ' Restartable property. 
 Set rstTemp = _ 
 .OpenRecordset("SELECT * FROM Employees") 
 Debug.Print "Recordset based on SQL statement" 
 Debug.Print " Restartable = " &amp; rstTemp.Restartable 
 rstTemp.Close 
 
 ' Open a Recordset from a saved QueryDef object and 
 ' print its Restartable property. 
 Set rstTemp = .OpenRecordset("Current Product List") 
 Debug.Print _ 
 "Recordset based on permanent QueryDef (" &amp; _ 
 rstTemp.Name &amp; ")" 
 Debug.Print " Restartable = " &amp; rstTemp.Restartable 
 rstTemp.Close 
 
 .Close 
 End With 
 
End Sub 

```


