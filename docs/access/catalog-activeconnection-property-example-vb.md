---
title: "Catalog ActiveConnection Property Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 12a34091-e451-dbd1-e7f3-f794b84ee5b0
description: "Setting the ActiveConnection property to a valid, open connectionopensthe catalog. From an open catalog, you can access the schema objects contained within that catalog."
---

# Catalog ActiveConnection Property Example (VB)

Setting the [ActiveConnection](activeconnection-property-adox.md) property to a valid, open connection "opens" the catalog. From an open catalog, you can access the schema objects contained within that catalog. 
  
```
 
' BeginOpenConnectionVB 
Sub OpenConnection() 
 On Error GoTo OpenConnectionError 
 
 Dim cnn As New ADODB.Connection 
 Dim cat As New ADOX.Catalog 
 
 cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source= 'c:\Program Files\Microsoft Office\" &amp; _ 
 "Office\Samples\Northwind.mdb';" 
 Set cat.ActiveConnection = cnn 
 Debug.Print cat.Tables(0).Type 
 
 'Clean up 
 cnn.Close 
 Set cat = Nothing 
 Set cnn = Nothing 
 Exit Sub 
 
OpenConnectionError: 
 
 Set cat = Nothing 
 
 If Not cnn Is Nothing Then 
 If cnn.State = adStateOpen Then cnn.Close 
 End If 
 Set cnn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndOpenConnectionVB 

```

Setting the **ActiveConnection** property to a valid connection string also "opens" the catalog. 
  
```
' BeginOpenConnection2VB 
Sub Main() 
 On Error GoTo OpenConnectionWithStringError 
 Dim cat As New ADOX.Catalog 
 
 cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "Data Source='c:\Program Files\Microsoft Office\" &amp; _ 
 "Office\Samples\Northwind.mdb';" 
 Debug.Print cat.Tables(0).Type 
 
 'Clean up 
 Set cat.ActiveConnection = Nothing 
 Exit Sub 
 
OpenConnectionWithStringError: 
 Set cat = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndOpenConnection2VB 

```


