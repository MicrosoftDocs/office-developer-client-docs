---
title: "Create Method Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 3e6a4f3d-3b25-2dfb-5ef3-6a4c5326b78f
description: "The following code shows how to create a new Microsoft Jet database with the Create method."
---

# Create Method Example (VB)

The following code shows how to create a new Microsoft Jet database with the [Create](create-method-adox.md) method. 
  
```
 
' BeginCreateDatabseVB 
Sub CreateDatabase() 
 On Error GoTo CreateDatabaseError 
 
 Dim cat As New ADOX.Catalog 
 cat.Create "Provider='Microsoft.Jet.OLEDB.4.0';Data Source='c:\new.mdb'" 
 
 'Clean up 
 Set cat = Nothing 
 Exit Sub 
 
CreateDatabaseError: 
 Set cat = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndCreateDatabaseVB 

```


