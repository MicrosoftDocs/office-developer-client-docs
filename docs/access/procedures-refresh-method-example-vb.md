---
title: "Procedures Refresh Method Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fd6d71cf-7a6b-49d7-220b-dd5b815a92ab
description: "The following code shows how to refresh the Procedures collection of a Catalog. This is required before Procedure objects from the Catalog can be accessed."
---

# Procedures Refresh Method Example (VB)

The following code shows how to refresh the [Procedures](procedures-collection-adox.md) collection of a [Catalog](catalog-object-adox.md). This is required before [Procedure](procedure-object-adox.md) objects from the **Catalog** can be accessed. 
  
```
 
' BeginProceduresRefreshVB 
Sub Main() 
 On Error GoTo ProcedureRefreshError 
 
 Dim cat As New ADOX.Catalog 
 
 ' Open the Catalog 
 cat.ActiveConnection = _ 
 "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source='c:\Program Files\" &amp; _ 
 "Microsoft Office\Office\Samples\Northwind.mdb';" 
 
 ' Refresh the Procedures collection 
 cat.Procedures.Refresh 
 
 'Clean up 
 Set cat.ActiveConnection = Nothing 
 Set cat = Nothing 
 Exit Sub 
 
ProcedureRefreshError: 
 Set cat = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndProceduresRefreshVB 

```


