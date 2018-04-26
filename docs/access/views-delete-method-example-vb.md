---
title: "Views Delete Method Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 423cd4e6-dfa5-8559-b1f3-b789a7aa9590
description: "The following code shows how to use the Delete method to delete a view from the catalog."
---

# Views Delete Method Example (VB)

The following code shows how to use the [Delete](delete-method-adox-collections.md) method to delete a view from the catalog. 
  
```
 
' BeginDeleteViewVB 
Sub Main() 
 On Error GoTo DeleteViewError 
 
 Dim cat As New ADOX.Catalog 
 
 ' Open the catalog 
 cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source='c:\Program Files\Microsoft Office\" &amp; _ 
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
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndDeleteViewVB 

```


