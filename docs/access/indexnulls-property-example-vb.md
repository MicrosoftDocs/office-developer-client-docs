---
title: "IndexNulls Property Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 69b5661c-931e-3a1c-d60e-96a0f93b9494
description: "This example demonstrates the IndexNulls property of an Index. The code creates a new index and sets the value of IndexNulls based on user input (from a list box named List1). Then, the Index is appended to the EmployeesTable in the NorthwindCatalog. The new Index is applied to a Recordset based on the Employees table, and the Recordset is opened. A new record is added to the Employees table, with a Null value in the indexed field. Whether this new record is displayed depends on the setting of the IndexNulls property."
---

# IndexNulls Property Example (VB)

This example demonstrates the [IndexNulls](indexnulls-property-adox.md) property of an [Index](index-object-adox.md). The code creates a new index and sets the value of **IndexNulls** based on user input (from a list box named List1). Then, the **Index** is appended to the **Employees**[Table](table-object-adox.md) in the  *Northwind* [Catalog](catalog-object-adox.md). The new **Index** is applied to a [Recordset](recordset-object-ado.md) based on the **Employees** table, and the **Recordset** is opened. A new record is added to the **Employees** table, with a **Null** value in the indexed field. Whether this new record is displayed depends on the setting of the **IndexNulls** property. 
  
```
' IndexNullsVB 
Sub Main() 
 On Error GoTo IndexNullsXError 
 
 Dim cnn As New ADODB.Connection 
 Dim catNorthwind As New ADOX.Catalog 
 Dim idxNew As New ADOX.Index 
 Dim rstEmployees As New ADODB.Recordset 
 Dim varBookmark As Variant 
 
 ' Connect the catalog. 
 cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source='c:\Program Files\" &amp; _ 
 "Microsoft Office\Office\Samples\Northwind.mdb';" 
 
 Set catNorthwind.ActiveConnection = cnn 
 
 ' Append Country column to new index 
 idxNew.Columns.Append "Country" 
 idxNew.Name = "NewIndex" 
 
 Dim Response 
 Response = MsgBox("Allow 'Null' index? Otherwise ignore 'Null' index.", vbYesNo) 
 '"Allow 'Null' index? Otherwise ignore 'Null' index." 
 ', vbYesNo + vbCritical + vbDefaultButton2,,,, 
 If Response = vbYes Then ' User chose Yes. 
 idxNew.IndexNulls = adIndexNullsAllow 
 Else ' User chose No. 
 idxNew.IndexNulls = adIndexNullsIgnore 
 End If 
 
 'Append new index to Employees table 
 catNorthwind.Tables("Employees").Indexes.Append idxNew 
 
 rstEmployees.Index = idxNew.Name 
 rstEmployees.Open "Employees", cnn, adOpenKeyset, _ 
 adLockOptimistic, adCmdTableDirect 
 
 With rstEmployees 
 ' Add a new record to the Employees table. 
 .AddNew 
 !FirstName = "Gary" 
 !LastName = "Haarsager" 
 .Update 
 
 ' Bookmark the newly added record 
 varBookmark = .Bookmark 
 
 ' Use the new index to set the order of the records. 
 .MoveFirst 
 
 Debug.Print "Index = " &amp; .Index &amp; _ 
 ", IndexNulls = " &amp; idxNew.IndexNulls 
 Debug.Print " Country - Name" 
 
 ' Enumerate the Recordset. The value of the 
 ' IndexNulls property will determine if the newly 
 ' added record appears in the output. 
 Do While Not .EOF 
 Debug.Print " " &amp; _ 
 IIf(IsNull(!Country), "[Null]", !Country) &amp; _ 
 " - " &amp; !FirstName &amp; " " &amp; !LastName 
 .MoveNext 
 Loop 
 
 ' Delete new record because this is a demonstration. 
 .Bookmark = varBookmark 
 .Delete 
 
 .Close 
 End With 
 
 'Clean up 
 Set rstEmployees = Nothing 
 catNorthwind.Tables("Employees").Indexes.Delete idxNew.Name 
 cnn.Close 
 Set cnn = Nothing 
 Set catNorthwind = Nothing 
 Set idxNew = Nothing 
 Exit Sub 
 
IndexNullsXError: 
 
 If Not rstEmployees Is Nothing Then 
 If rstEmployees.State = adStateOpen Then rstEmployees.Close 
 End If 
 Set rstEmployees = Nothing 
 
 ' Delete new Index because this is a demonstration. 
 If Not catNorthwind Is Nothing Then 
 catNorthwind.Tables("Employees").Indexes.Delete idxNew.Name 
 End If 
 
 If Not cnn Is Nothing Then 
 If cnn.State = adStateOpen Then cnn.Close 
 End If 
 Set cnn = Nothing 
 
 Set catNorthwind = Nothing 
 Set idxNew = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
 
End Sub 
' EndIndexNullsVB 

```


