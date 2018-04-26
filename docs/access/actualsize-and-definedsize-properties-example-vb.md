---
title: "ActualSize and DefinedSize Properties Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: fc268c63-c4b3-f633-1efb-aaf88354efd4
description: "This example uses the ActualSize and DefinedSize properties to display the defined size and actual size of a field."
---

# ActualSize and DefinedSize Properties Example (VB)

This example uses the [ActualSize](actualsize-property-ado.md) and [DefinedSize](definedsize-property-ado.md) properties to display the defined size and actual size of a field. 
  
```
 
'BeginActualSizeVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'recordset and connection variables 
 Dim rstStores As ADODB.Recordset 
 Dim SQLStores As String 
 Dim strCnxn As String 
 'record variables 
 Dim strMessage As String 
 
 ' Open a recordset for the Stores table 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Northwind';Integrated Security='SSPI';" 
 Set rstStores = New ADODB.Recordset 
 
 SQLStores = "Suppliers" 
 rstStores.Open SQLStores, strCnxn, adOpenForwardOnly, adLockReadOnly, adCmdTable 
 'the above two lines of code are identical as the default values for 
 'CursorType and LockType arguments match those indicated 
 
 ' Loop through the recordset displaying the contents 
 ' of the store_name field, the field's defined size, 
 ' and its actual size. 
 rstStores.MoveFirst 
 
 Do Until rstStores.EOF 
 strMessage = "Company name: " &amp; rstStores!CompanyName &amp; _ 
 vbCrLf &amp; "Defined size: " &amp; _ 
 rstStores!CompanyName.DefinedSize &amp; _ 
 vbCrLf &amp; "Actual size: " &amp; _ 
 rstStores!CompanyName.ActualSize &amp; vbCrLf 
 
 MsgBox strMessage, vbOKCancel, "ADO ActualSize Property (Visual Basic)" 
 rstStores.MoveNext 
 Loop 
 
 ' clean up 
 rstStores.Close 
 Set rstStores = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rstStores Is Nothing Then 
 If rstStores.State = adStateOpen Then rstStores.Close 
 End If 
 Set rstStores = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
'EndActualSizeVB 

```


