---
title: Procedures Delete method example (VB)
TOCTitle: Procedures Delete method example (VB)
ms:assetid: 1cbae0a2-0035-d03f-b9c6-5453ddd51ec4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248964(v=office.15)
ms:contentKeyID: 48543576
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Procedures Delete method example (VB)


**Applies to**: Access 2013, Office 2013

The following code demonstrates how to delete a procedure using the [Procedures](procedures-collection-adox.md) collection [Delete](delete-method-adox-collections.md) method.

```vb 
 
' BeginDeleteProcedureVB 
Sub Main() 
 On Error GoTo DeleteProcedureError 
 
 Dim cat As New ADOX.Catalog 
 
 ' Open the Catalog. 
 cat.ActiveConnection = _ 
 "Provider='Microsoft.Jet.OLEDB.4.0';" & _ 
 "Data Source='c:\Program Files\Microsoft Office\" & _ 
 "Office\Samples\Northwind.mdb';" 
 
 ' Delete the Procedure. 
 cat.Procedures.Delete "CustomerById" 
 
 'Clean up 
 Set cat.ActiveConnection = Nothing 
 Set cat = Nothing 
 Exit Sub 
 
DeleteProcedureError: 
 Set cat = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
End Sub 
' EndDeleteProcedureVB 
```

