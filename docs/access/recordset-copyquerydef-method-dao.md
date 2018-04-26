---
title: "Recordset.CopyQueryDef Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fee8c2fe-500e-dfb3-21ce-211e54ff334b
description: "Returns a QueryDef object that is a copy of the QueryDef used to create the Recordset object represented by the recordset placeholder (Microsoft Access workspaces only). ."
---

# Recordset.CopyQueryDef Method (DAO)

Returns a **[QueryDef](querydef-object-dao.md)** object that is a copy of the **QueryDef** used to create the **[Recordset](recordset-object-dao.md)** object represented by the  _recordset_ placeholder (Microsoft Access workspaces only). . 
  
## Syntax

 *expression*  . **CopyQueryDef**
  
 *expression*  A variable that represents a **Recordset** object. 
  
### Return Value

QueryDef
  
## Remarks

You can use the **CopyQueryDef** method to create a new **QueryDef** that is a duplicate of the **QueryDef** used to create the **Recordset**. 
  
If a **QueryDef** wasn't used to create this **Recordset**, an error occurs. You must first open a **Recordset** with the **OpenRecordset** method before using the **CopyQueryDef** method. 
  
This method is useful when you create a **Recordset** object from a **QueryDef**, and pass the **Recordset** to a function, and the function must re-create the SQL equivalent of the query, for example, to modify it in some way. 
  
## Example

This example uses the **CopyQueryDef** method to create a copy of a **QueryDef** from an existing **Recordset** and modifies the copy by adding a clause to the SQL property. When you create a permanent **QueryDef**, spaces, semicolons, or linefeeds may be added to the SQL property; these extra characters must be stripped before any new clauses can be attached to the SQL statement. 
  
```
Function CopyQueryNew(rstTemp As Recordset, _ 
 strAdd As String) As QueryDef 
 
 Dim strSQL As String 
 Dim strRightSQL As String 
 
 Set CopyQueryNew = rstTemp.CopyQueryDef 
 With CopyQueryNew 
 ' Strip extra characters. 
 strSQL = .SQL 
 strRightSQL = Right(strSQL, 1) 
 Do While strRightSQL = " " Or strRightSQL = ";" Or _ 
 strRightSQL = Chr(10) Or strRightSQL = vbCr 
 strSQL = Left(strSQL, Len(strSQL) - 1) 
 strRightSQL = Right(strSQL, 1) 
 Loop 
 .SQL = strSQL &amp; strAdd 
 End With 
 
End Function 
 
This example shows 

```

This example shows a possible use of CopyQueryNew().
  
```
Sub CopyQueryDefX() 
 
 Dim dbsNorthwind As Database 
 Dim qdfEmployees As QueryDef 
 Dim rstEmployees As Recordset 
 Dim intCommand As Integer 
 Dim strOrderBy As String 
 Dim qdfCopy As QueryDef 
 Dim rstCopy As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set qdfEmployees = dbsNorthwind.CreateQueryDef( _ 
 "NewQueryDef", "SELECT FirstName, LastName, " &amp; _ 
 "BirthDate FROM Employees") 
 Set rstEmployees = qdfEmployees.OpenRecordset( _ 
 dbOpenForwardOnly) 
 
 Do While True 
 intCommand = Val(InputBox( _ 
 "Choose field on which to order a new " &amp; _ 
 "Recordset:" &amp; vbCr &amp; "1 - FirstName" &amp; vbCr &amp; _ 
 "2 - LastName" &amp; vbCr &amp; "3 - BirthDate" &amp; vbCr &amp; _ 
 "[Cancel - exit]")) 
 Select Case intCommand 
 Case 1 
 strOrderBy = " ORDER BY FirstName" 
 Case 2 
 strOrderBy = " ORDER BY LastName" 
 Case 3 
 strOrderBy = " ORDER BY BirthDate" 
 Case Else 
 Exit Do 
 End Select 
 Set qdfCopy = CopyQueryNew(rstEmployees, strOrderBy) 
 Set rstCopy = qdfCopy.OpenRecordset(dbOpenSnapshot, _ 
 dbForwardOnly) 
 With rstCopy 
 Do While Not .EOF 
 Debug.Print !LastName &amp; ", " &amp; !FirstName &amp; _ 
 " - " &amp; !BirthDate 
 .MoveNext 
 Loop 
 .Close 
 End With 
 Exit Do 
 Loop 
 
 rstEmployees.Close 
 ' Delete new QueryDef because this is a demonstration. 
 dbsNorthwind.QueryDefs.Delete qdfEmployees.Name 
 dbsNorthwind.Close 
 
End Sub 
 
```


