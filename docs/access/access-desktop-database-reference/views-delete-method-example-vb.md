---
title: Views Delete Method Example (VB)
TOCTitle: Views Delete Method Example (VB)
ms:assetid: 423cd4e6-dfa5-8559-b1f3-b789a7aa9590
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249194(v=office.15)
ms:contentKeyID: 48544474
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Views Delete Method Example (VB)


_**Applies to:** Access 2013 | Office 2013_

The following code shows how to use the [Delete](delete-method-adox-collections.md) method to delete a view from the catalog.

``` 
 
' BeginDeleteViewVB 
Sub Main() 
 On Error GoTo DeleteViewError 
 
 Dim cat As New ADOX.Catalog 
 
 ' Open the catalog 
 cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _ 
 "Data Source='c:\Program Files\Microsoft Office\" & _ 
 "Office\Samples\Northwind.mdb';" 
 
 'Delete the View 
 cat.Views.Delete "AllCustomers" 
 
 'Clean up 
 Set cat.ActiveConnection = Nothing 
 Set cat = Nothing 
 Exit Sub 
 
DeleteViewError: 
 Set cat = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
End Sub 
' EndDeleteViewVB 
```

