---
title: "Views Refresh Method Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 607b78d6-1b26-d643-9f97-f47b5f5cffc5
description: "The following code shows how to refresh the Views collection of a Catalog. This is required before View objects from the Catalog can be accessed."
---

# Views Refresh Method Example (VB)

The following code shows how to refresh the [Views](views-collection-adox.md) collection of a [Catalog](catalog-object-adox.md). This is required before [View](view-object-adox.md) objects from the **Catalog** can be accessed. 
  
```
 
' BeginViewsRefreshVB 
Sub Main() 
 On Error GoTo ProcedureViewsRefreshError 
 
 Dim cat As New ADOX.Catalog 
 
 ' Open the Catalog 
 cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source='c:\Program Files\" &amp; _ 
 "Microsoft Office\Office\Samples\Northwind.mdb';" 
 
 ' Refresh the Procedures collection 
 cat.Views.Refresh 
 
 'Clean up 
 Set cat = Nothing 
 Exit Sub 
 
ProcedureViewsRefreshError: 
 
 If Not cat Is Nothing Then 
 Set cat = Nothing 
 End If 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndViewsRefreshVB 

```


