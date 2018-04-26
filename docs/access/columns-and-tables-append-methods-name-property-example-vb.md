---
title: "Columns and Tables Append Methods, Name Property Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 39458400-f30c-0636-19f2-c2c2788a6534
description: "The following code demonstrates how to create a new table."
---

# Columns and Tables Append Methods, Name Property Example (VB)

The following code demonstrates how to create a new table.
  
```
 
' BeginCreateTableVB 
Sub Main() 
 On Error GoTo CreateTableError 
 
 Dim tbl As New Table 
 Dim cat As New ADOX.Catalog 
 
 ' Open the Catalog. 
 cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source='c:\Program Files\Microsoft Office\" &amp; _ 
 "Office\Samples\Northwind.mdb';" 
 
 tbl.Name = "MyTable" 
 tbl.Columns.Append "Column1", adInteger 
 tbl.Columns.Append "Column2", adInteger 
 tbl.Columns.Append "Column3", adVarWChar, 50 
 cat.Tables.Append tbl 
 Debug.Print "Table 'MyTable' is added." 
 
 'Delete the table as this is a demonstration. 
 cat.Tables.Delete tbl.Name 
 Debug.Print "Table 'MyTable' is deleted." 
 
 'Clean up 
 Set cat.ActiveConnection = Nothing 
 Set cat = Nothing 
 Set tbl = Nothing 
 Exit Sub 
 
CreateTableError: 
 
 Set cat = Nothing 
 Set tbl = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndCreateTableVB 

```


