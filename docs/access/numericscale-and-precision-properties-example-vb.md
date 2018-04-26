---
title: "NumericScale and Precision Properties Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 728a76a3-1f80-935b-b6c7-94255ffe0160
description: "This example demonstrates the NumericScale and Precision properties of the Column object. This code displays their value for the Order Details table of the Northwind database."
---

# NumericScale and Precision Properties Example (VB)

This example demonstrates the [NumericScale](numericscale-property-adox.md) and [Precision](precision-property-adox.md) properties of the [Column](column-object-adox.md) object. This code displays their value for the **Order Details** table of the  *Northwind*  database. 
  
```
 
' BeginNumericScalePrecVB 
Sub Main() 
 On Error GoTo NumericScalePrecXError 
 
 Dim cnn As New ADODB.Connection 
 Dim cat As New ADOX.Catalog 
 Dim tblOD As ADOX.Table 
 Dim colLoop As ADOX.Column 
 
 ' Connect the catalog. 
 cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _ 
 "data source='c:\Program Files\" &amp; _ 
 "Microsoft Office\Office\Samples\Northwind.mdb';" 
 Set cat.ActiveConnection = cnn 
 
 ' Retrieve the Order Details table 
 Set tblOD = cat.Tables("Order Details") 
 
 ' Display numeric scale and precision of 
 ' small integer fields. 
 For Each colLoop In tblOD.Columns 
 If colLoop.Type = adSmallInt Then 
 MsgBox "Column: " &amp; colLoop.Name &amp; vbCr &amp; _ 
 "Numeric scale: " &amp; _ 
 colLoop.NumericScale &amp; vbCr &amp; _ 
 "Precision: " &amp; colLoop.Precision 
 End If 
 Next colLoop 
 
 'Clean up 
 cnn.Close 
 Set cat = Nothing 
 Set cnn = Nothing 
 Exit Sub 
 
NumericScalePrecXError: 
 Set cat = Nothing 
 
 If Not cnn Is Nothing Then 
 If cnn.State = adStateOpen Then cnn.Close 
 End If 
 Set cnn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
' EndNumericScalePrecVB 

```


