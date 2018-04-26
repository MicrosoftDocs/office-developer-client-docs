---
title: "DBEngine.Idle Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052978
  
localization_priority: Normal
ms.assetid: c90b565e-626e-139d-102a-0386601ce0c8
description: "Suspends data processing, enabling the Microsoft Access database engine to complete any pending tasks, such as memory optimization or page timeouts (Microsoft Access workspaces only)."
---

# DBEngine.Idle Method (DAO)

Suspends data processing, enabling the Microsoft Access database engine to complete any pending tasks, such as memory optimization or page timeouts (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **Idle**( ** *Action* ** ) 
  
 *expression*  A variable that represents a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Action_ <br/> |Optional  <br/> |**Variant** <br/> |Specifies the action to take. Can be one of the **[IdleEnum](idleenum-enumeration-dao.md)** constants.  <br/> |
   
## Remarks

The **Idle** method allows the Microsoft Access database engine to perform background tasks that may not be up-to-date because of intense data processing. This is often true in multiuser, multitasking environments that don't have enough background processing time to keep all records in a **[Recordset](recordset-object-dao.md)** current. 
  
Usually, read locks are removed and data in local dynaset-type **Recordset** objects are updated only when no other actions (including mouse movements) occur. If you periodically use the **Idle** method, the Microsoft Access database engine can catch up on background processing tasks by releasing unneeded read locks. 
  
Specifying the optional **dbRefreshCache** argument refreshes memory with only the most current data from the database. 
  
You don't need to use this method in single-user environments unless multiple instances of an application are running. The **Idle** method may increase performance in a multiuser environment because it forces the database engine to write data to disk, releasing locks on memory. 
  
> [!NOTE]
> You can also release read locks by making operations part of a transaction. 
  
## Example

This example uses the **Idle** method to ensure that an output procedure is accessing the most current data available from the database. The IdleOutput procedure is required for this procedure to run. 
  
```
Sub IdleX() 
 
 Dim dbsNorthwind As Database 
 Dim strCountry As String 
 Dim strSQL As String 
 Dim rstOrders As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 ' Get name of country from user and build SQL statement 
 ' with it. 
 strCountry = Trim(InputBox("Enter country:")) 
 strSQL = "SELECT * FROM Orders WHERE ShipCountry = '" &amp; _ 
 strCountry &amp; "' ORDER BY OrderID" 
 
 ' Open Recordset object with SQL statement. 
 Set rstOrders = dbsNorthwind.OpenRecordset(strSQL) 
 
 ' Display contents of Recordset object. 
 IdleOutput rstOrders, strCountry 
 
 rstOrders.Close 
 dbsNorthwind.Close 
 
End Sub 
 
Sub IdleOutput(rstTemp As Recordset, strTemp As String) 
 
 ' Call the Idle method to release unneeded locks, force 
 ' pending writes, and refresh the memory with the current 
 ' data in the .mdb file. 
 DBEngine.Idle dbRefreshCache 
 
 ' Enumerate the Recordset object. 
 With rstTemp 
 Debug.Print "Orders from " &amp; strTemp &amp; ":" 
 Debug.Print , "OrderID", "CustomerID", "OrderDate" 
 Do While Not .EOF 
 Debug.Print , !OrderID, !CustomerID, !OrderDate 
 .MoveNext 
 Loop 
 End With 
 
End Sub 
 
```


