---
title: "Recordset2.Transactions Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f2169565-f782-4089-0e4b-bc5d58d37db5
description: "Returns a value that indicates whether an object supports transactions. Read-only Boolean ."
---

# Recordset2.Transactions Property (DAO)

Returns a value that indicates whether an object supports transactions. Read-only **Boolean**. 
  
## Syntax

 *expression*  . **Transactions**
  
 *expression*  A variable that represents a **Recordset2** object. 
  
## Remarks

In a Microsoft Access workspace, you can also use the **Transactions** property with dynaset- or table-type **Recordset** objects. Snapshot- and forward-only-type **[Recordset](recordset-object-dao.md)** objects always return **False**. 
  
If a dynaset- or table-type **Recordset** is based on a Microsoft Access database engine table, the **Transactions** property is **True** and you can use transactions. Other database engines may not support transactions. For example, you can't use transactions in a dynaset-type **Recordset** object based on a Paradox table. 
  
Check the **Transactions** property before using the **[BeginTrans](dbengine-begintrans-method-dao.md)** method on the **Recordset** object's **[Workspace](workspace-object-dao.md)** object to make sure that transactions are supported. Using the **BeginTrans**, **CommitTrans**, or **Rollback** methods on an unsupported object has no effect. 
  
## Example

This example demonstrates the **Transactions** property in Microsoft Access workspaces. 
  
```
Sub TransactionsX() 
 
 Dim wrkAcc As Workspace 
 Dim dbsNorthwind As Database 
 Dim conPubs As Connection 
 Dim rstTemp As Recordset 
 
 Set wrkAcc = CreateWorkspace("", "admin", "", dbUseJet) 
 Set dbsNorthwind = wrkAcc.OpenDatabase("Northwind.mdb") 
 
 ' Open two different Recordset objects and display the 
 ' Transactions property of each. 
 
 Debug.Print "Opening Microsoft Access table-type " &amp; _ 
 "recordset..." 
 Set rstTemp = dbsNorthwind.OpenRecordset( _ 
 "Employees", dbOpenTable) 
 Debug.Print " Transactions = " &amp; rstTemp.Transactions 
 
 Debug.Print "Opening forward-only-type " &amp; _ 
 "recordset where the source is an SQL statement..." 
 Set rstTemp = dbsNorthwind.OpenRecordset( _ 
 "SELECT * FROM Employees", dbOpenForwardOnly) 
 Debug.Print " Transactions = " &amp; rstTemp.Transactions 
 
 rstTemp.Close 
 dbsNorthwind.Close 
 conPubs.Close 
 wrkAcc.Close 
End Sub 
 
```


