---
title: "Clustered Property Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 1065622d-9473-209a-95be-c4b0ab5b687a
description: "This example demonstrates the Clustered property of an Index. Note that Microsoft Jet databases do not support clustered indexes, so this example will return False for the Clustered property of all indexes in the Northwind database."
---

# Clustered Property Example (VB)

This example demonstrates the [Clustered](clustered-property-adox.md) property of an [Index](index-object-adox.md). Note that Microsoft Jet databases do not support clustered indexes, so this example will return **False** for the **Clustered** property of all indexes in the  *Northwind*  database. 
  
```
 
' BeginClusteredVB 
Sub Main() 
 On Error GoTo ClusteredXError 
 
 Dim cnn As New ADODB.Connection 
 Dim cat As New ADOX.Catalog 
 Dim tblLoop As ADOX.Table 
 Dim idxLoop As ADOX.Index 
 Dim strCnn As String 
 
 strCnn = "Provider='SQLOLEDB';Data Source='MySqlServer';Initial Catalog='pubs';" &amp; _ 
 "Integrated Security='SSPI';" 
 ' Connect the catalog. 
 cnn.Open strCnn 
 cat.ActiveConnection = cnn 
 
 ' Enumerate Tables 
 For Each tblLoop In cat.Tables 
 'Enumerate Indexes 
 For Each idxLoop In tblLoop.Indexes 
 Debug.Print tblLoop.Name &amp; " " &amp; _ 
 idxLoop.Name &amp; " " &amp; idxLoop.Clustered 
 Next idxLoop 
 Next tblLoop 
 
 'Clean up 
 cnn.Close 
 Set cat = Nothing 
 Set cnn = Nothing 
 Exit Sub 
 
ClusteredXError: 
 
 Set cat = Nothing 
 
 If Not cnn Is Nothing Then 
 If cnn.State = adStateOpen Then cnn.Close 
 End If 
 Set cnn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndClusteredVB 

```


